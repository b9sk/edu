## Примеры работы с wget

#### Скачать одну страницу
`wget -k -x -p --no-parent --adjust-extension https://www.example.com/index.php`  

#### Скачать сайт целиком
`wget -r -x -p -k --no-parent --adjust-extension https://www.example.com/index.php`  


#### Запрос cookie и отправка cookie
Здесь следует выполнить две последовательные команды. Сначала берем и сохраняем куки с главной страницы. Второй командой запускаем краулинг, указывая файл сookie.
```
# Первый запрос, который скачает только одну страницу и отключится.
# cookies.txt должен включать абсолютный путь, если wget запускаеся через cron
wget --save-cookies cookies.txt --adjust-extension https://www.example.com/index.php

# Пример второго запроса
wget --load-cookies cookies.txt -k -r -x -p --no-parent --adjust-extension --level=999 --wait=8 --random-wait https://www.example.com/index.php
```


## Параметры
`-k`, `--convert-links` меняет url в документах на относительные  
`-x` создавать папки, если необходимо  
`-p` загружать все файлы, которые нужны для отображения страниц HTML: изображения, css, js  
`-r` рекурсивный обход  
`--no-parent` не подниматься на уровень выше  
`--adjust-extension` добавлять расширение .html к файлам без него  
`--no-clobber`, `-nc` Не скачивать страницу, если есть на диске  
`--wait=10 --random-wait` ждать в диапазоне от (0.5\*10) до (1.5\*10) перед выполнением запроса  
`--level=depth` максимальная глубина при рекурсивном обходе. по-умолчению равна 5  
`--no-verbose`, `-nv` выключает отчет (verbose), но ошибки будут выводится  
`--quiet` полностью выключает вывод  
`-i file|-` читает из файла или stdin. Каждый url должен быть с новой строки.  
`-H`, `--span-hosts` скачивает картинки (не только), которые находятся на другом хосте (поддомене)
`-e robots=off` не искать robots.txt
`--header="Header: value"` заголовков может быть несколько


### User Agent
`--user-agent`, `-U` по-умолчанию отправляет `Wget/version`  
`--user-agent=""` не отправлять UA  

#### Яндекс-Бот
`--user-agent="Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)"`  
#### Chrome *
`--user-agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"`
#### Chrome Android
`--user-agent="Mozilla/5.0 (Linux; Android 6.0; M5c Build/MRA58K) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/62.0.3202.84 Mobile Safari/537.36"`

* Свежую версию можно получить через JS браузера: `navigator.userAgent`  


### Cookie
https://askubuntu.com/a/161814


### Исключения
`-A acclist --accept acclist`
`-R rejlist --reject rejlist`
Specify comma-separated lists of file name suffixes or patterns to accept or reject. Note that if any of the wildcard characters, `*`, `?`, `[` or `]`, appear in an element of acclist or rejlist, it will be treated as a pattern, rather than a suffix.  In this case, you have to enclose the pattern into quotes to prevent your shell from expanding it, like in `-A "*.mp3"` or `-A '*.mp3'`.  
Пример: `-A *.html -R *.gz, *.tar`
`-X folder_list` исключить папки. Пример: `-X /public_html/videos,/public_html/audio`


### Отладка
`-d` показывать отправленные и полученные заголовки. Полезно во время подготовки.  
`--rejected-log=logfile` Logs all URL rejections to logfile as comma separated values.  The values include the reason of rejection, the URL and the parent URL it was found in. **Не отлавливает ошибки типа 5xx!"**