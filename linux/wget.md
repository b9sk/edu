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
`-k (--convert-links)` меняет url в документах на относительные  
`-x` создавать папки, если необходимо  
`-p` загружать все файлы, которые нужны для отображения страниц HTML: изображения, css, js  
`-r` рекурсивный обход  
`--no-parent` не подниматься на уровень выше  
`--adjust-extension` добавлять расширение .html к файлам без него (рекомендуется в windows)  
`--reject="robots.txt"` не качать этот файл (поддерживает маски).  
`--no-clobber` Не скачивать страницу, если есть на диске
`--wait=10 --random-wait` ждать в диапазоне от (0.5\*10) до (1.5\*10) перед выполнением запроса  
`--user-agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/61.0.3163.100 Safari/537.36"` свежую версию можно получить через JS браузера: `navigator.userAgent`  
`--level=depth` максимальная глубина при рекурсивном обходе. по-умолчению равна 5  

#### Отладка
`-d` показывать отправленные и полученные заголовки. Полезно во время подготовки.