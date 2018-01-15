### Команды npm
Собрать промежуточный результат, удобный для отладки стилей  
`npm start`

Собрать готовый результат, включая inline стили  
`npm run build`

Собрать и отправить все html из папки /dist/
`npm run mail[ -- --to="mail@example.com"]`

### Скруглить края таблицы
Изменить правило у table, в которой нужно скруглить края:  
`table { border-collapse: separate; }`

### Выключить минификацию кода (`gulpfile.babel.js`):  
```javascript
    .pipe($.htmlmin, {
      collapseWhitespace: false,
      minifyCSS: false
    });
```

### Выключить адаптивность
`src/assets/scss/foundation-emails.scss`: убрать `@import 'components/media-query';`
`src/layouts/default.html`: убрать `<meta name="viewport" content="width=device-width">`

### Использовать шаблон, отличный от layouts/default.html
```
---
layout: another-layout
---
```