# Файл mkdocs.yml

Файл mkdocs.yml — это конфиг, определяющий основные параметры проекта.

Он создаётся в формате yaml, предназначенном для структурированной записи информации в виде пар ключ: значение

По умолчанию в конфиге прописан один параметр:

`site_name: My Docs`

Для полноценной настройки проекта добавьте в конфиг другие параметры:

1. Основные параметры сайта и темы:

```markdown title= "mkdocs.yml начало"

site_name: Novillero portfolio # Название сайта
site_description: Профессиональное портфолио # Описание сайта, добавляется в meta-теги
theme: # Тема сайта, информация о ее параметрах
  name: material # Название темы
  logo: images/logo.svg # Ссылка на логотип сайта, логотип добавляется в папку `docs/images`
  font:
    text: Roboto # Шрифт текста
    code: Roboto Mono # Шрифт для текста кода
  language: ru # Язык
  palette: # Настройки светлой и тёмной тем
    # Настройки светлой темы
    - scheme: default 
      toggle:
        icon: material/weather-sunny # Иконка для активации светлой темы
        name: Выключить солнышко # Всплывающий текст-подсказка
      primary: blue # Основной цвет
      accent: purple # Акцентный цвет
      # вы можете использовать любой цвет из списка: 
      # red; pink; purple; deep purple; indigo; blue; light blue; cyan; teal; 
      # green; light green; lime; yellow; amber; orange; deep orange; brown; 
      # grey; blue grey; black; white

    # Настройки тёмной темы
    - scheme: slate
      toggle:
        icon: material/weather-night
        name: Позвать солнышко
      primary: deep purple
      accent: blue
  features: # настройки функциональностей темы
    - navigation.sections # Добавление разделов верхнего уровня в боковом меню, отключение спойлеров в боковом меню
    - navigation.path # Хлебные крошки
    - navigation.indexes # Позволяет создавать корневые страницы разделов меню. Корневая страница должна лежать в папке раздела и называться index.md. Пример использования корневых страниц приведен ниже в настройках nav
    - navigation.tabs # Верхнее меню
    - navigation.tabs.sticky # Фиксация верхнего меню
    - navigation.expand # Разворачивает спойлеры в левом меню по умолчанию
    - toc.integrate # Фиксирует оглавление страницы в левом меню
    - navigation.instant # Функция быстрой загрузки страниц
    - navigation.top # Добавляет кнопку «к началу» для быстрой обратной прокрутки страницы
    - search.suggest # Подсказки при вводе поискового запроса
    - search.highlight # Подсветка результатов поиска в тексте страницы
    - content.code.copy # Кнопка копирования в блоке кода
```
2. Навигация. В этом разделе конфига настраивается структура сайта. Здесь вы должны указать все статьи, которые будут добавлены в док.портал, с учётом их вложенности:

```markdown title= "mkdocs.yml продолжение"

nav: # Структура сайта
- Главная страница: index.md
- 'Markdown: базовый синтаксис': markdown.md
- Тех.минимум по git: git-for-tech-writer.md
- Стайлгайд для пошаговых инструкций: styleguide.md
- Домашний проект:
  - pet-project/index.md # корневая страница подраздела; работает при включенной функции navigation.indexes
  - Настройка MkDocs: pet-project/mkdocs-setup.md # вложенные страницы отбиваются отступами
- Вебинары: meetings.md
- Домашние задания:
  - Домашнее задание №0: homeworks/homework-0.md
  - Домашнее задание N1: homeworks/homework-1.md
  - Домашнее задание N2: homeworks/homework-2.md
```

3. Расширения markdown (в примере приведены наиболее употребляемые расширения):

```markdown title= "mkdocs.yml продолжение"

markdown_extensions: # Расширения markdown
  - admonition # Поддержка информационных панелей (сообщений типа «Внимание», «Совет», «Примечание», etc.)
  - footnotes # Поддержка встроенных сносок на страницах
  - attr_list # Использование html-атрибутов и CSS в элементах markdown
  - md_in_html # Поддержка markdown внутри html
  - def_list # Поддержка списков определений
  - pymdownx.tabbed: # Использование вкладок (табов)
      alternate_style: true
  - pymdownx.details # Использование спойлеров (катов)
  - pymdownx.highlight: # Подсветка синтаксиса в блоках кода
      anchor_linenums: true
  - pymdownx.superfences # Поддержка вложенных блоков кода
  - pymdownx.emoji: # Иконки и эмодзи
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
```

4. Плагины. В разделе подключаются модульные плагины для добавления новых функциональностей:

```markdown title= "mkdocs.yml продолжение"

plugins:
  - search # Плагин для подключения поиска на портале
```

!!! note "Примечание"
    Для работы плагина его нужно предварительно установить через Python installs Packages (pip).