### ������� npm
������� ������������� ���������, ������� ��� ������� ������  
`npm start`

������� ������� ���������, ������� inline �����  
`npm run build`

������� � ��������� ��� html �� ����� /dist/
`npm run mail[ -- --to="mail@example.com"]`

### ��������� ���� �������
�������� ������� � table, � ������� ����� ��������� ����:  
`table { border-collapse: separate; }`

### ��������� ����������� ���� (`gulpfile.babel.js`):  
```javascript
    .pipe($.htmlmin, {
      collapseWhitespace: false,
      minifyCSS: false
    });
```

### ��������� ������������
`src/assets/scss/foundation-emails.scss`: ������ `@import 'components/media-query';`
`src/layouts/default.html`: ������ `<meta name="viewport" content="width=device-width">`

### ������������ ������, �������� �� layouts/default.html
```
---
layout: another-layout
---
```