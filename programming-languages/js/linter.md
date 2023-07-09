# 🖊 Linter

## Online tools

check and fix - [https://validatejavascript.com/](https://validatejavascript.com/)

## ESlint

link - [https://eslint.org](https://eslint.org/)

### Setup

```
npm init @eslint/config
```

### Current config

`.eslintrc.json`

```json
{
    "env": {
        "browser": true,
        "es2021": true,
        "node": true
    },
    "extends": "google",
    "overrides": [
    ],
    "parserOptions": {
        "ecmaVersion": "latest"
    },
    "rules": {
    }
}

```
