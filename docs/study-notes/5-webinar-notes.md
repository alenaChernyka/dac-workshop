# Подключение разных типов документации к проекту

## Openapi

### Swagger

1. Скачать плагин для обработки спецификаций openapi

    `pip install mkdocs-swagger-ui-tags`

2. Подключить в yml

    `plugins`

3. В файле swagger.md (добавить в навигацию)

    `<swagger-ui src='openapi.yaml'`

4. Запустить mkdocs

    `mkdocs serve`

5. Сделать спецификацию на всю ширину страницы

    ```yaml
    ---
    hide:
        -toc
    ---
    ```

### Redoc

1. Установить

    `pip install mkdocs-redoc`

2. Подключить в конфиге

3. Файл redoc.md (прописать в навигации)

    `<redoc src='openapi.yml'`

4. Запустить mkdocs

    `mkdocs serve`

5. Сделать спецификацию на всю ширину страницы и убрать навигацию

    ```yaml
    ---
    hide:
        -toc
        -navigation
    ---
    ```

    Обновить воркфлоу в ci.yml

    ```yaml
    - run: pip install mkdocs-swagger-ui-tag
    - run: pip install mkdocs-redoc
    ```

## Диаграммы UML

### Создать диаграмму

1. Представить участников

    ```
    actor Пользователь as user
    participant Приложение as client
    participant Бэк as server
    database "База данных" as db
    ```

2. Добавить действия

    ```
    user -> client: Нажимает кнопку "Создать новую"
    client --> user: Открывает форму создания заметки
    user -> client: Заполняет форму и нажимает "Сохранить"
    client -> server: Запрос POST http.//notesapp.su/api/notes
    server -> db: Сохраняет заметку
    server <-- db: Сообщает, что заметка сохранена
    client <-- server: 201 OK
    user <-- client: Открывает уведомление\n "Заметка успешно сохранена"
    ```

    - запросы прямой линией
    - ответы пунктирной
    - стрелки можно рисовать в обратном направлении

3. Добавить альтернативный сценарий

    ```
    alt Отказ пользователя
    user -> client: Нажимает кнопку "Создать новую"
    user <-- client: Открывает форму создания заметки
    user -> client: Нажимает кнопку "Отменить"
    user <-- client: Открывает главный экран
    end alt
    ```

### Сделать диаграмму в проекте

1. Создать diagram.md с заголовком "Диаграмма последовательности", добавить в навигацию в конфиге
2. Скопировать текст диаграммы в блок кода с языком puml
3. Установить плагин

    `pip install mkdocs_puml`

4. Подключить плагин в конфиге yml

    ```yaml
    plugins:
        -plantuml:
            puml-url: ссылка
        
    ```

5. Добавить шаг в воркфлоу

    `- run: pip install mkdocs_puml`

    alt shift - большой курсор