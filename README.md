# minimarket-api

API de práctica gratuita con los datos de un pequeño supermercado, pensada para aprender a consumir APIs desde Android (Retrofit, Ktor...) o cualquier otra plataforma.

Son archivos JSON en un repositorio público de GitHub: no hace falta registrarse ni tener clave. Es de solo lectura.

## URLs

| Recurso | URL |
| --- | --- |
| Productos | https://raw.githubusercontent.com/0winDev/minimarket-api/main/data/products.json |
| Promociones | https://raw.githubusercontent.com/0winDev/minimarket-api/main/data/promotions.json |

Para Retrofit, usa como `baseUrl`:

```
https://raw.githubusercontent.com/0winDev/minimarket-api/main/
```

Y como rutas `data/products.json` y `data/promotions.json`.

## Datos

### products.json

40 productos de 9 categorías.

```json
{
  "products": [
    {
      "id": "p1",
      "name": "Leche Entera 1L",
      "category": "Dairy",
      "priceCents": 120,
      "stock": 0,
      "imageUrl": "https://images.unsplash.com/photo-1580910051074-3eb694886505"
    }
  ]
}
```

- `priceCents`: precio en céntimos (`120` = 1,20 €).
- `stock`: unidades disponibles. Hay productos con `0` para practicar el estado "agotado".
- `category`: `Bakery`, `Cleaning`, `Dairy`, `Drinks`, `Frozen`, `Fruits`, `Meat`, `Pantry` o `Snacks`.

### promotions.json

15 promociones asociadas a productos.

```json
{
  "promotions": [
    {
      "id": "promo2",
      "productId": "p2",
      "type": "BUY_X_PAY_Y",
      "percent": null,
      "buyX": 2,
      "payY": 1,
      "startAtEpoch": 1700000000,
      "endAtEpoch": 1893456000
    }
  ]
}
```

- `productId`: el `id` del producto al que se aplica.
- `type`: `PERCENT` (usa `percent`) o `BUY_X_PAY_Y` (usa `buyX` y `payY`). El campo que no aplica viene a `null`.
- `startAtEpoch` / `endAtEpoch`: inicio y fin en segundos (epoch). Hay promociones activas, caducadas y futuras a propósito.

## Ideas para practicar

- Mostrar el precio en euros a partir de `priceCents`.
- Marcar como agotados los productos sin stock.
- Filtrar por categoría.
- Mostrar solo las promociones activas según la fecha actual.
- Calcular el precio final de cada producto con su promoción.

## Crea la tuya

¿Quieres montar una API así para tu propia app? Tienes la guía paso a paso en [owindev.dev](https://owindev.dev/blog/api-gratis-github-android).
