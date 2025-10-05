```go
package main

import "github.com/gin-gonic/gin"

type Product struct {
    ID    int    `json:"id"`
    Name  string `json:"name"`
    Price int    `json:"price"`
}

var products = []Product{
    {1, "Ноутбук", 50000},
    {2, "Мышь", 1000},
}

func main() {
    r := gin.Default()
    
    // GET - получить все продукты
    r.GET("/products", func(c *gin.Context) {
        c.JSON(200, gin.H{
            "products": products,
        })
    })
    
    // GET - получить продукт по ID
    r.GET("/products/:id", func(c *gin.Context) {
        id := c.Param("id")
        
        // Ищем продукт (упрощенный пример)
        for _, product := range products {
            if fmt.Sprintf("%d", product.ID) == id {
                c.JSON(200, product)
                return
            }
        }
        
        c.JSON(404, gin.H{"error": "Продукт не найден"})
    })
    
    // POST - добавить новый продукт
    r.POST("/products", func(c *gin.Context) {
        var newProduct Product
        
        if err := c.ShouldBindJSON(&newProduct); err != nil {
            c.JSON(400, gin.H{"error": "Неверные данные"})
            return
        }
        
        // Добавляем продукт
        products = append(products, newProduct)
        
        c.JSON(201, gin.H{
            "status": "Продукт добавлен",
            "product": newProduct,
        })
    })
    
    r.Run()
}
```