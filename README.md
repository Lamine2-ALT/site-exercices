# Exercices imprimables

Site web statique pour parcourir, rechercher, filtrer et imprimer des exercices scolaires.

## Contenu

- `index.html` — liste des exercices (recherche + filtre par niveau)
- `exercice.html` — page dédiée d’un exercice (affichage + impression)
- `exercices.json` — données des exercices
- `assets/style.css` — styles (écran et impression)
- `.gitignore` — fichiers ignorés par Git

## Prérequis

Un serveur HTTP local est nécessaire, car `fetch` ne fonctionne pas de façon fiable en ouvrant les fichiers via `file://`.

## Tester localement

Depuis le dossier du projet :

```bash
# Avec Python 3
python -m http.server 8000
```

Puis ouvrez [http://localhost:8000](http://localhost:8000) dans le navigateur.

Autres options :

```bash
# Avec Node.js (npx)
npx serve .

# Avec PHP
php -S localhost:8000
```

## Ajouter un exercice

1. Ouvrez `exercices.json`.
2. Ajoutez un nouvel objet dans le tableau, avec les champs suivants :

| Champ         | Description                                      |
|---------------|--------------------------------------------------|
| `id`          | Identifiant unique (utilisé dans l’URL)          |
| `titre`       | Titre affiché                                    |
| `niveau`      | Niveau scolaire (ex. `6ème`, `5ème`)             |
| `description` | Court résumé pour la liste                       |
| `html`        | Contenu HTML de l’exercice (affiché tel quel)    |

Exemple :

```json
{
  "id": "tables-multiplication",
  "titre": "Tables de multiplication",
  "niveau": "CE2",
  "description": "Révisions des tables de 2 à 9.",
  "html": "<h2>Tables de multiplication</h2><ol><li>3 × 4 = ____</li><li>7 × 8 = ____</li></ol>"
}
```

3. Enregistrez le fichier et rechargez la page d’accueil.

## Impression

Sur la page d’un exercice, cliquez sur **Imprimer**. Les éléments portant la classe `no-print` (navigation, boutons, barre d’outils) sont masqués grâce à `@media print` dans `assets/style.css`.

## Stack

HTML, CSS et JavaScript vanilla uniquement — aucun framework, aucun backend.
