# Тестовое задание: Веб-сервис для управления автомобилями

## 🎯 Цель
Создать веб-сервер на Go для работы с информацией об автомобилях. Сервис должен предоставлять REST API для создания, получения и управления данными об автомобилях.
Задача этого тестового задания - проверить твои навыки. Если чего-то не знаешь - не страшно, сделай как умеешь.
После выполнения задания мы с тобой его разберем

## 📋 Требования

### 🔧 Технические требования
- Язык: **Golang**
- Хранение данных: **in-memory** (слайс или мапа)
- Валидация: нужно валидировать данные, которые присылает пользователь
  - `mark` и `model` - обязательные поля, минимум 1 символ
  - `owner_count` - не отрицательное число
  - `price` - положительное число
  - `currency` - валидные коды валют (RUB, USD, EUR)
  - `options` - должен быть не пустой
- Ошибки: будет здорово если попробуешь добавить обработку ошибок (как умеешь)
- Можно использовать любые библиотеки/фреймворки
- **Запрещено использовать ИИ** для генерации кода

## 🌐 API Endpoints

### Создание автомобиля
- Method: `POST`
- URL: `/cars/add`
- Request Body:
```json
{
  "mark": "bmw",
  "model": "3 series",
  "owner_count": 5,
  "price": 2593,
  "currency": "RUB",
  "options": ["Adaptive Cruise Control", "Heated and Ventilated Seats", "Heads-Up Display"]
}
```
- Response:
```json
{
  "id": 1
}
```

### Получение автомобиля по ID
- Method: `GET`
- URL: `/cars/{id}`
- Response:
```json
{
  "id": 1,
  "mark": "bmw",
  "model": "3 series",
  "owner_count": 5,
  "price": 2593,
  "currency": "RUB",
  "options": ["Adaptive Cruise Control", "Heated and Ventilated Seats", "Heads-Up Display"]
}
```

### Получение всех автомобилей
- Method: `GET`
- URL: `/cars`
- Response
```json
[
  {
    "id": 1,
    "mark": "bmw",
    "model": "3 series",
    "owner_count": 5,
    "price": 2593,
    "currency": "RUB",
    "options": ["Adaptive Cruise Control", "Heated and Ventilated Seats", "Heads-Up Display"]
  }
]
```

### Удаление автомобиля по ID
- Method: `DELETE`
- URL: `/cars/{id}`
- Response
```json
{
    "message": "success"
}
```