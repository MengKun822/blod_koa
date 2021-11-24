# 用 vite 搭建 vue3+TS 项目

### 步骤一：初始化项目

```
npm init vite-app my_blog
```

### 步骤二：安装 TS 依赖

```
npm install typescript
```

在根目录中穿件 tsconfig.json 文件

```json
{
    "compilerOptions": {
        "target": "esnext",
        "module": "esnext",
        "strict": "true",
        "jsx": "preserve",
        "moduleResolution": "node"
    },
    "include": ["src/**/*", "src/main.d.ts"],
    "exclude": ["node_modules"]
}
```

修改 src/main.js 为 src.main.ts

修改根目录下的 index.html 中引入的 main.js 为 main.ts

在根目录下创建 vue.config.js 文件,修改项目的入口文件为 main.ts,

```js
module.exports = {
    pages: {
        index: {
            entry: 'src/main.ts',
        },
    },
};
```

在 src 目录下创建一个.d.ts 文件名后缀的文件来定义.vue 文件

```ts
declare module '*.vue' {
    import { App, defineComponent } from 'vue';
    const component: ReturnType:<typeof defineComponent> {
        install(app: App):viod;
    };
    export default component;
}
```
