# React + TypeScript + Vite

本模板提供在 Vite 中使用 React 的最小配置，包含 HMR 及部分 ESLint 规则。

当前官方插件包括：

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md)：使用 [Babel](https://babeljs.io/) 实现 Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc)：使用 [SWC](https://swc.rs/) 实现 Fast Refresh

## 扩展 ESLint 配置

若开发生产环境应用，建议启用类型感知的 lint 规则：

```js
export default tseslint.config({
    extends: [
        // 移除 ...tseslint.configs.recommended 并替换为：
        ...tseslint.configs.recommendedTypeChecked,
        // 或使用更严格的规则
        ...tseslint.configs.strictTypeChecked,
        // 可选：样式相关规则
        ...tseslint.configs.stylisticTypeChecked,
    ],
    languageOptions: {
        // 其他选项...
        parserOptions: {
            project: ['./tsconfig.node.json', './tsconfig.app.json'],
            tsconfigRootDir: import.meta.dirname,
        },
    },
});
```

也可安装 [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) 与 [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) 以使用 React 专用 lint 规则：

```js
// eslint.config.js
import reactX from 'eslint-plugin-react-x';
import reactDom from 'eslint-plugin-react-dom';

export default tseslint.config({
    plugins: {
        'react-x': reactX,
        'react-dom': reactDom,
    },
    rules: {
        ...reactX.configs['recommended-typescript'].rules,
        ...reactDom.configs.recommended.rules,
    },
});
```
