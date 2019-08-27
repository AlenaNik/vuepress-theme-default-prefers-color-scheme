## 介绍

vuepress-theme-default-prefers-color-scheme 是一款为 [vuepress 默认主题](https://v1.vuepress.vuejs.org/zh/theme/default-theme-config.html) 增加 `浅色` 与 `深色` 主题的一款主题

## 原理

主要是基于下一代 css 技术中的 [prefers-color-scheme](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@media/prefers-color-scheme) 与 [CSS Variables](https://developer.mozilla.org/zh-CN/docs/Web/CSS/--*) 实现。

#### 查看支持浏览器

- [prefers-color-scheme](https://www.caniuse.com/#search=prefers-color-scheme)
- [CSS Variables](https://www.caniuse.com/#search=CSS%20Variables)

**对于 `prefers-color-scheme` 还需要你的操作系统支持切换浅色与深色模式**

- mac Mojave ^10.14
- windows 10 ^1809

**对于都不支持的浏览器将显示与默认主题几乎相同的样式**

## 安装

``` sh
yarn add vuepress-theme-default-prefers-color-scheme
# or
npm i vuepress-theme-default-prefers-color-scheme
```

## 使用

``` js {3}
// .vuepress -> config.js
module.exports = {
  theme: 'default-prefers-color-scheme',
  themeConfig: {
    // ...
  }
}
```

## 配置

### defaultTheme
- Type: `string`, `object`
- Default: `undefined`
- Required: `false`

::: tip
默认情况下，要显示浅色或深色主题由 [prefers-color-scheme](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme) 决定, 你可以通过设置 `defaultTheme` 来指定显示的主题颜色。基于 [css-prefers-color-scheme](https://github.com/csstools/css-prefers-color-scheme)
:::

支持 `light`, `dark` 或者 `{ theme: [begin hours, end hours] }`

``` js {4,6,8}
module.exports = {
  theme: 'default-prefers-color-scheme',
  themeConfig: {
    defaultTheme: 'dark',
    // or
    defaultTheme: { dark: [18, 6] },
    // or
    defaultTheme: { light: [6, 18], dark: [18, 6] },
  },
  // 当你指定了显示主题的颜色时，你需要增加如下的 postcss 插件
  postcss: {
    plugins: [
      require('css-prefers-color-scheme/postcss'),
      require('autoprefixer')
    ]
  }
}
```

其它配置与 [官方主题配置](https://v1.vuepress.vuejs.org/theme/default-theme-config.html) 相同

## 样式

在 `.vuepress/styles/palette.styl`  文件里你可以对 [默认预设的样式](https://github.com/tolking/vuepress-theme-default-prefers-color-scheme/blob/master/styles/palette.styl) 应用简单的颜色替换

**`$accentColor` 和 `$accentDarkColor` 最好被一起更改**
