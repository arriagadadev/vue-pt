# Prueba técnica Frontend Developer (vue)

## ¿Qué se busca evaluar?
* Creatividad para resolver los requerimientos
* Calidad del código entregado (estructura y buenas prácticas)
* Eficiencia de los algoritmos entregados
* Familiaridad con el stack de desarrollo y autentificación de APIs

## Objetivo

Crear una app web que contenga un CRUD de items de un inventario, haciendo uso de la API REST de prueba que se encuentra en este mismo archivo (README.md).

## Requerimientos

* Crear CRUD de items (crear, enlistar, editar, eliminar)
* Utilizar Vue 2 como framework frontend
* Usar Vuetify como biblioteca de componentes
* Usar Vue Router y Vuex donde se considere necesario
* Implementar al menos dos vistas
* Utilizar la información del endpoint "/categories" para construir el selector de categorías en la vista de edición/creación de items
* No es necesario incluir un paginador, es suficiente con que se muestre la primera página
* No es necesario incluir un login, se puede usar un token estático

## Deseable

* Usar Actions de Vuex para hacer las llamadas a API

## Fuente de datos

A continuación se detallan los endpoints, el contenido de sus solicitudes y el contenido de sus respuestas.
También se puede hacer uso de este [Postman Collection](https://drive.google.com/file/d/15-pksgpBg7bWDLhmGEWa_wpD0QotRa8R/view?usp=sharing) que concentra la misma información.

Endpoint base: https://pt.arriagada.dev/api

Método de autenticación: Bearer TOKEN

Email: demo@demo.cl

Password: demo

#### POST /login

Headers:
Accept: application/json
Content-Type: application/json

##### Request body:
```javascript
{
    "email": "demo@demo.cl",
    "password": "demo"
}
```

##### Response:
```javascript
{
    "user": {
        "id": 1,
        "name": "Demo User",
        "email": "demo@demo.cl",
        "email_verified_at": null,
        "created_at": "2021-04-27T13:19:22.000000Z",
        "updated_at": "2021-04-27T13:19:22.000000Z"
    },
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9...."
}
```

#### GET /items

Headers:
Accept: application/json
Content-Type: application/json
Authorization: Bearer [TOKEN]

##### Response:
```javascript
{
    "current_page": 1,
    "data": [
        {
            "id": 11,
            "name": "GALAX GeForce GTX 1050 Ti (1-Click OC) 128-bit DDR5",
            "quantity": "1244",
            "status": "1"
        },
        {
            "id": 10,
            "name": "ZOTAC GAMING GeForce GTX 1660 SUPER Twin Fan 6GB GDDR6",
            "quantity": "252",
            "status": "1"
        },
        ...
    ],
    "first_page_url": "https://pt.arriagada.dev/api/items?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "https://pt.arriagada.dev/api/items?page=1",
    "next_page_url": null,
    "path": "https://pt.arriagada.dev/api/items",
    "per_page": 15,
    "prev_page_url": null,
    "to": 11,
    "total": 11
}
```

#### GET /item/{itemId}

Headers:
Accept: application/json
Content-Type: application/json
Authorization: Bearer [TOKEN]

##### Response:
```json
{
    "id": 1,
    "name": "ASUS ROG STRIX Z490-E Gaming",
    "description": "Lorem ipsum dolor sit amet consectetur...",
    "quantity": 223,
    "categoryId": 1,
    "priceTaxExcluded": 361,
    "status": 0
}
```

#### POST /item

##### Body request:
```javascript
{
    "name": "ASUS ROG STRIX Z490-E Gaming",
    "description": "Lorem ipsum dolor sit amet consectetur...",
    "quantity": 223,
    "categoryId": 1,
    "priceTaxExcluded": 361,
    "status": 0
}
```
##### Response:
```javascript
{
    "name": "ASUS ROG STRIX Z490-E Gaming",
    "description": "Lorem ipsum dolor sit amet consectetur...",
    "quantity": 223,
    "category_id": 1,
    "price_tax_excluded": 361,
    "status": 0,
    "updated_at": "2021-07-31T21:28:45.000000Z",
    "created_at": "2021-07-31T21:28:45.000000Z",
    "id": 1
}
```

#### PUT /item

##### Body request:
```javascript
{
    "id": 1,
    "name": "ASUS ROG STRIX Z490-E Gaming",
    "description": "Lorem ipsum dolor sit amet consectetur...",
    "quantity": 223,
    "categoryId": 1,
    "priceTaxExcluded": 361,
    "status": 0
}
```
##### Response:
```javascript
{
    "id": 1,
    "name": "ASUS ROG STRIX Z490-E Gaming",
    "description": "Lorem ipsum dolor sit amet consectetur...",
    "quantity": 223,
    "category_id": 1,
    "price_tax_excluded": 361,
    "status": 0,
    "created_at": "2021-07-31T20:51:49.000000Z",
    "updated_at": "2021-07-31T21:30:01.000000Z"
}
```

#### DELETE /item/{itemId}

##### Response:
```javascript
{
    "message": "This item was deleted successfully"
}
```

#### GET /categories

##### Response:
```javascript
[
    {
        "id": 1,
        "name": "Motherboard"
    },
    {
        "id": 2,
        "name": "Cabinet"
    },
    {
        "id": 3,
        "name": "RAM"
    },
    {
        "id": 4,
        "name": "Cooling System"
    },
    ...
]
```

## Cómo entregar
* Clonar este repositorio en su máquina local
* Crear una nueva rama utilizando su nombre completo
* Crear una pull request de esa rama
