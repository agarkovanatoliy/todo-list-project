# React + TypeScript + Vite

Этот шаблон предоставляет минимальную настройку для работы React в Vite с HMR и некоторыми правилами ESLint.

В настоящее время доступны два официальных плагина:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) использует [Babel](https://babeljs.io/) для быстрого обновления
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) использует  [SWC](https://swc.rs/) для быстрого обновления

## Расширение конфигурации ESLint

Если вы разрабатываете производственное приложение,  рекомендуется обновить конфигурацию, чтобы включить правила линтинга с учетом типа:

- Настройте верхний уровень `parserOptions` свойство, как это:

```js
export default tseslint.config({
  languageOptions: {
    // другие варианты...
    parserOptions: {
      project: ["./tsconfig.node.json", "./tsconfig.app.json"],
      tsconfigRootDir: import.meta.dirname,
    },
  },
});
```

- Заменить `tseslint.configs.recommended` на `tseslint.configs.recommendedTypeChecked` или `tseslint.configs.strictTypeChecked`
- По желанию добавьте `...tseslint.configs.stylisticTypeChecked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) и обновите конфигурацию:

```js
// eslint.config.js для быстрого обновления
import react from "eslint-plugin-react";

export default tseslint.config({
  // Установите версию react
  settings: { react: { version: "18.3" } },
  plugins: {
    // Добавьте плагин react
    react,
  },
  rules: {
    // Другие правила...
    // Включите рекомендуемые правила
    ...react.configs.recommended.rules,
    ...react.configs["jsx-runtime"].rules,
  },
});
```
