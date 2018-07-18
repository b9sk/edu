### Множественное число в javascript

```javascript
declOfNum(n, words) {
  return titles[(n % 10 === 1 && n % 100 !== 11) ? 0 : n % 10 >= 2 && n % 10 <= 4 && (n % 100 < 10 || n % 100 >= 20) ? 1 : 2]
}

var apples = declOfNum(['Яблоко','Яблока','Яблок']);
apples(0) // Яблок
apples(1) // Яблоко
apples(2) // Яблока
```

[Больше языков](http://docs.translatehouse.org/projects/localization-guide/en/latest/l10n/pluralforms.html?id=l10n/pluralforms)

[Источник](https://gist.github.com/realmyst/1262561#gistcomment-2299442)