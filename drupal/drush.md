## Установка Drupal в Ubuntu 16.04

### Требования
`php-xml php-gd`

### Выбор и загрузка дистрибутива
`drush dl drupal-7 --select`

### Установка скачаного дистрибутива
```
cd drupal-7.XX
drush si standard --db-url=mysql://[db_user]:[db_pass]@[ip-address]/[db_name]
```

## Доступ из любой папки
`drush --root=/var/www/html --uri=mysite.org dl module`

## Бекап

### Сохранить файлы и базу
`drush archive-dump[|ard] --destination=./dumps/filename.tar`

### Бекап из архива обратно в папку
`drush archive-restore[|arr] ./example.tar.gz --destination=/var/www/example.com/docroot`

### После бекапа!
```
sudo chmod -R 777 sites/default/files/styles
sudo chmod 777 sites/default/files/ctools
```

## Обновление

1. выключить сайт:
`drush vset maintenance_mode 1`  
2. обновление ядра:
`drush pm-update drupal`  
3. обновление модулей:
`drush up`  
4. включить сайт:
`drush vset maintenance_mode 0`


## Отладка темы (см. в Dev tools браузера)
```
drush vset theme_debug 1
drush vset theme_debug 0
```

## Создание полей
`drush field-create content-type machine_name,fieldtype[,widget_name]`

## Работа с модулями
Загрузить и включить модуль:
```
drush dl module_name
drush en module_name
```

## Список модулей
`drush pm-list --type=Module [--status=enabled]`
