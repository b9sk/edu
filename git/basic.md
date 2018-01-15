Привязать ssh-ключ к удаленному репозиторию (Linux)
===================================================
1. Создать ключ как обычно
2. Сохранить публичный ключ в профиле пользователя github (bitbucket)
3. Связать ключ с доменом через ~/.ssh/config:
```
Host preferredName
    HostName bitbucket.org
    User git
    IdentityFile ~/.ssh/id_rsa
```
5. Добавить удаленный репозиторий:  
`git remote add origin git@server.remote:/path/to/repo.git`
6. Отправить локальный репозиторий на удаленный:  
`git push -u origin master`


Работа с репозиториями
======================

Список ЛОКАЛЬНЫХ веток, где активная помечена звездочкой  
`git branch --list`

Показать удаленный репозиторий  
`git remote`  
`git remote -v`  
`git branch -r`  

Показать УДАЛЕННЫЙ И ЛОКАЛЬНЫЙ репозитории  
`git branch -a`  

Добавить удаленный репозиторий из существующего локального (см. примеры github или bitbucket)  
`git remote add origin user@server.remote:/path/to/repo.git`

Удалить удаленный репозиторий  
`git remote remove origin`


Работа с ветками
================

Создать ветку и переключиться на неё  
`git checkout -b name_of_new_branch`

Переключиться на ветку master  
`git checkout master`


Работа с файлами
================

Удалить файл из репозитория, но оставить его на диске  
`git rm --cached <file>`

Удалить все файлы из текущего кеша  
`git rm -r --cached .`

Удалить новые _неотслеживаемые_ файли и папки  
`git clean -df`

Не удалять, но посмотреть что будет удалено  
`git clean -dfn`


Pull
====

Если нужно перезаписать локальные файлы принудительно  
`git fetch --all`
`git reset --hard origin/master`


Лог
===

Краткий формат  
`git log --pretty[=short|full|fuller]`

Показывает ветвление  
`git log --graph`


diff
====

Показать разницу между последним коммитом и текущим состоянием  
`git diff`

Показать разницу между последним и ПРЕДпоследним коммитами  
`git diff HEAD^ HEAD`