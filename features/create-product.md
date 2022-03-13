[← Back](../README.md)

# Création produit

## Description

En tant que vendeur, j'aimerais pouvoir mettre mes produits en vente.

## Critères de succès

- Le titre n'est pas vide.
- La description n'est pas vide.
- Le produit est associé à une catégorie.
- Le prix suggéré minimum est 1$.
- Le nouveau produit possède un identifiant **unique**.
- Le nouveau produit possède une date de création non-modifiable.
- Le nouveau produit est sauvegardé dans l'application.
- Le nouveau produit ne contient pas d'offres.

## Détails techniques

### Requête

**Route**

`POST /products`

**Headers**

- `X-Seller-Id` : ID du vendeur qui créer le produit
  - type: `string`

**Body**

```ts
{
  title: string,
  description: string,
  suggestedPrice: number,
  category: ProductCategory
}
```

**Exemple**

```json
{
  "title": "Nice hairbrush",
  "description": "Pink and all.",
  "suggestedPrice": 34.21,
  "category": "beauty",
}
```

### Réponse

**Status**

`201 CREATED`

**Headers**

- `Location` : URI du nouveau vendeur
  - type : `string`
  - format : `<baseUrl>/products/<productId>`
  - exemples
    - `http://localhost:8080/products/123`
    - `http://splendid-tasteful-leak.herokuapp.com/products/123`

### Exceptions

- `MISSING_PARAMETER` si un champ de la requête est manquant.
- `INVALID_PARAMETER` si un des champs de la requête est invalide.
- `ITEM_NOT_FOUND` si le vendeur associé à `X-Seller-Id` n'existe pas.
