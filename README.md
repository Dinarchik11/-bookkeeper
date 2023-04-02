# Простая программа для управления личными финансами
#### (учебный проект для курса по практике программирования на Python)

[Техническое задание](specification.md)

Архитектура проекта строится на принципе инверсии зависимостей. Упрощенная схема
классов выглядит так:
![](structure.png)

Для хранения данных используется паттерн Репозиторий. Структура файлов
и каталогов (модулей и пакетов) отражает архитектуру:

📁 bookkeeper - исполняемый код 

- 📁 models - модели данных

    - 📄 budget.py - бюджет
    - 📄 category.py - категория расходов
    - 📄 expense.py - расходная операция
- 📁 repository - репозиторий для хранения данных

    - 📄 abstract_repository.py - описание интерфейса
    - 📄 memory_repository.py - репозиторий для хранения в оперативной памяти
    - 📄 sqlite_repository.py - репозиторий для хранения в sqlite (пока не написан)
- 📁 view - графический интерфейс (пока не написан)
- 📄 simple_client.py - простая консольная утилита, позволяющая посмотреть на работу программы в действии
- 📄 utils.py - вспомогательные функции

📁 tests - тесты (структура каталога дублирует структуру bookkeeper)

Для работы с проектом нужно сделать fork и склонировать его себе на компьютер.

Проект создан с помощью poetry. Убедитесь, что poetry у вас установлена
(инструкцию по установке можно посмотреть [здесь](https://python-poetry.org/docs/)).
Для установки всех зависимостей, запустите (убедитесь, что вы находитесь
в корневой папке проекта - там, где лежит файл pyproject.toml):

```commandline
poetry install
```

Для запуска тестов и статических анализаторов используйте следующие команды (убедитесь, 
что вы находитесь в корневой папке проекта):
```commandline
poetry run pytest --cov
poetry run mypy --strict bookkeeper
poetry run pylint bookkeeper
poetry run flake8 bookkeeper
```
Отдельно нужно установить PySide6.

Программа запускается в main.py