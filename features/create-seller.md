[← Back](../README.md)

# Création vendeur

## Description

En tant que vendeur, je peux me créer un compte afin d'accéder aux fonctionnalités de l'application.

## Critères de succès

- Les informations du vendeur ne sont pas vides.
- Le vendeur a 18 ans ou plus.
- Le nouveau vendeur est sauvegardé dans l'application.
- Le nouveau vendeur possède un identifiant **unique**.
- Le nouveau vendeur possède une date de création non-modifiable.

## Détails techniques

### Requête

**Route**

`POST /sellers`

**Body**

```ts
{
  name: string,
  birthdate: Date,
  email: Email,
  phoneNumber: PhoneNumber,
  bio: string,
}
```

**Exemple**

```json
{
  "name": "John Doe",
  "birthdate": "1968-09-12",
  "email": "john.doe123@gmail.com",
  "phoneNumber": "14181234567",
  "bio": "A simple man.",
}
```

### Réponse

**Status**

`201 CREATED`

**Headers**

- `Location` : URI du nouveau vendeur
  - type : `string`
  - format : `<baseUrl>/sellers/<sellerId>`
  - exemples
    - `http://localhost:8080/sellers/abc`
    - `http://splendid-tasteful-leak.herokuapp.com/sellers/abc`

### Exceptions

- `MISSING_PARAMETER` si un champ de la requête est manquant.
- `INVALID_PARAMETER` si un des champs de la requête est invalide.
