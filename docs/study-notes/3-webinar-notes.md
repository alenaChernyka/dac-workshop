# Создание домашнего док проекта

## Создать локальный репозиторий
1. Создать папку
2. В папке открыть командную строку или открыть в vscode правой кнопкой
3. git init

## Mkdocs material

1. `pip install mkdocs`
2. `pip install mkdocs-material`
3. `mkdocs new .`
4. появился конфиг yaml и папка docs
5. `mkdocs serve` запустить сборку


`![](/images)`
`![](../images)` относительная ссылка

## Yaml

```
site_name: (для метатега title) Мой пет-проект
site_description: (для метатега desription) Пет-проект по мастер-классу
```


```
theme:
	name: material
	logo: images/logo.svg
	favicon: (?)
	font:
		text: Roboto
		code: Roboto Mono
	language: ru
	pallette: (настройка цветовой схемы - тем)
	features: (настройки функциональности темы)
		не оставлять все функции включенными  — они конфликтуют
```

```
nav: (что будет указано в меню)
	- Главная страница: index.md
	- PIP: pip.md
	- Пошаговые инструкции:
		- instructions/index.md
		- Установка mkdocs: instructions/mkdocs.md
```

```
markdown_extensions:
	
```

```
plugins:
	- search:
```

## Далее

1. выключить `mkdocs serve Ctrl+C`
2. сохраняем в гите на всех уровнях (кроме последнего)
3. создать удаленный репозиторий на гитхабе
4. скопировать ссылку на репозиторий
5. git remote add origin ссылка
6. git push
7. git push -u origin (то же самое что --set-upstream)