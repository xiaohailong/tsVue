# tsVue
vuecli with typescript

### vsCode markdown preview 
1. commoand+shift+p 
2. input markdown 
3. choose 'Markdown: Open Preview to the Side'  


###  vue-cli 3 use pug template
```html
<template lang="pug">
    .divWraper  content
        .innerDiv content
</template>
<!--identify-->
<template lang="pug">
    <div class="divWraper">
        content
        <div class="innerDiv">content<div>
    </div>
</template>

more usage see [pug](https://pugjs.org/zh-cn/api/getting-started.html)

```
install pug dependencies
```
npm i -D pug pug-html-loader pug-plain-loader
```

add webpack setting in vue.config.js

if vue.config.js not exist,please add it

```js
module.exports = {
    chainWebpack: config => {
        config.module.rule('pug')
            .test(/\.pug$/)
            .use('pug-html-loader')
            .loader('pug-html-loader')
            .end()
    }
}
```