# Файл mkdocs.yml

Файл `mkdocs.yml` — это конфиг, определяющий основные параметры проекта.

Он создаётся в формате YAML, предназначенном для структурированной записи информации в виде пар «ключ: значение».

По умолчанию в конфиге прописан один параметр:

```yaml
site_name: My Docs
```

Для полноценной настройки проекта добавьте в конфиг другие параметры.

### 1. Основные параметры сайта и темы

```yaml title="mkdocs.yml — начало"
site_name: Novillero portfolio # Название сайта
site_description: Профессиональное портфолио # Описание сайта, добавляется в meta-теги

theme: # Тема сайта, информация о её параметрах
  name: material # Название темы
  logo: images/logo.svg # Ссылка на логотип сайта, логотип добавляется в папку docs/images
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

    # Настройки тёмной темы
    - scheme: slate
      toggle:
        icon: material/weather-night
        name: Позвать солнышко
      primary: deep purple
      accent: blue

  features: # Настройки функциональностей темы
    - navigation.sections
    - navigation.path
    - navigation.indexes
    - navigation.tabs
    - navigation.tabs.sticky
    - navigation.expand
    - toc.integrate
    - navigation.instant
    - navigation.top
    - search.suggest
    - search.highlight
    - content.code.copy
```

### 2. Навигация

В этом разделе конфига настраивается структура сайта. Здесь указываются все статьи, которые будут добавлены в док.портал, с учётом их вложенности:

```yaml title="mkdocs.yml — продолжение"
nav: # Структура сайта
  - Главная страница: index.md
  - 'Markdown: базовый синтаксис': markdown.md
  - Тех.минимум по Git: git-for-tech-writer.md
  - Стайлгайд для пошаговых инструкций: styleguide.md
  - Домашний проект:
      - pet-project/index.md # Корневая страница подраздела; работает при включенной функции navigation.indexes
      - Настройка MkDocs: pet-project/mkdocs-setup.md # Вложенные страницы отбиваются отступами
  - Вебинары: meetings.md
  - Домашние задания:
      - Домашнее задание №0: homeworks/homework-0.md
      - Домашнее задание №1: homeworks/homework-1.md
      - Домашнее задание №2: homeworks/homework-2.md
```

### 3. Расширения Markdown

В примере приведены наиболее употребляемые расширения:

```yaml title="mkdocs.yml — продолжение"
markdown_extensions: # Расширения Markdown
  - admonition # Поддержка информационных панелей
  - footnotes # Поддержка встроенных сносок на страницах
  - attr_list # Использование HTML-атрибутов и CSS в элементах Markdown
  - md_in_html # Поддержка Markdown внутри HTML
  - def_list # Поддержка списков определений
  - pymdownx.tabbed: # Использование вкладок
      alternate_style: true
  - pymdownx.details # Использование спойлеров
  - pymdownx.highlight: # Подсветка синтаксиса в блоках кода
      anchor_linenums: true
  - pymdownx.superfences # Поддержка вложенных блоков кода
  - pymdownx.emoji: # Иконки и эмодзи
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
```

### 4. Плагины

В разделе подключаются плагины для добавления новых функциональностей:

```yaml title="mkdocs.yml — продолжение"
plugins:
  - search # Плагин для подключения поиска на портале
```

!!! note "Примечание"

    Для работы плагина его нужно предварительно установить через Python с помощью `pip`.