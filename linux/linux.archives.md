## Zip
`zip [-rq] zipfilename folder/` [-x pattern]

### Параметры
`-rq` - рекурсивно и тихо
`-x file|pattern` - исключить файл или папку, используя маску. Можно указывать несколько раз.

#### Примеры
`-x .\*` - exclude all files beginning with a dot

`-x \*.\*` - exclude all files (with a dot in the filename)

`-x app/bower_components/\* -x node_modules/\*` - exclude this directory and all files in it

`-x \*.zip` - exclude all zip-Files