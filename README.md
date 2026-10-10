# oxlint-config-react-app

Configuration [oxlint](https://oxc.rs/docs/guide/usage/linter.html) + [oxfmt](https://oxc.rs/docs/guide/usage/formatter.html) partagée pour applications React / TypeScript.

Rédigée à partir de zéro pour les projets personnels de samsam00z — sans code tiers propriétaire.

## Utilisation dans un projet

1. Installer le paquet :

```shell
npm i -D github:samsam00z/oxlint-config-react-app
```

2. Créer `.oxlintrc.jsonc` à la racine du projet :

```jsonc
{
  "extends": [
    "node_modules/oxlint-config-react-app/.oxlintrc.json"
  ]
}
```

3. Créer `.oxfmtrc.jsonc` à la racine du projet :

```jsonc
{
  "extends": [
    "node_modules/oxlint-config-react-app/.oxfmtrc.json"
  ]
}
```

4. Scripts dans `package.json` :

```json
{
  "scripts": {
    "lint": "oxlint",
    "format": "oxfmt",
    "format:check": "oxfmt --check"
  }
}
```

5. Optionnel — formater + corriger avant chaque commit (avec husky + lint-staged) :

```json
{
  "lint-staged": {
    "*.{ts,tsx}": "npx oxfmt && npx oxlint --fix"
  }
}
```

## Contenu

- `categories` : `correctness` et `perf` en erreur, `suspicious` et `style` en avertissement
- Limites de complexité : `complexity` 12, `max-depth` 3, `max-params` 4, `max-lines` 400, `max-lines-per-function` 120
- Imports de types cohérents (`consistent-type-imports`), promesses flottantes surveillées
- Règles React : `jsx-key` en erreur, composants auto-fermés
- Règles unicorn utiles (`prefer-includes`, `prefer-string-replace-all`)
- Assouplissements automatiques pour les fichiers de test (`*.test.*`, `*.spec.*`, `__tests__/`)

Toutes les règles se surchargent dans le `.oxlintrc.jsonc` du projet — voir la [doc oxlint](https://oxc.rs/docs/guide/usage/linter.html).

## Licence

MIT
