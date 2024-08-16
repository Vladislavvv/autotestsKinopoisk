# Автоматизация тестирования API и UI для веб-приложения
## Описание проекта
Этот проект содержит набор автоматизированных тестов для API и UI веб-приложения Кинопоиск. Тесты разработаны с использованием pytest, requests, selenium, и allure, что позволяет обеспечить качественную проверку функционала приложения. Основная цель — автоматизировать тестирование ключевых аспектов работы приложения для повышения его стабильности и ускорения разработки.

## Структура проекта
test_api.py: Тесты для проверки API эндпоинтов.
test_ui.py: Тесты для проверки UI функционала.
search_page.py: Класс Page Object для взаимодействия с элементами страницы поиска.
settings.py: Файл с базовым URL для UI тестов.
config.py: Конфигурационный файл с базовым URL и заголовками для API тестов.
requirements.txt: Список необходимых для проекта зависимостей.

## Установка зависимостей
Для начала работы с проектом необходимо установить все зависимости:
pip install -r requirements.txt

## Конфигурация
### Файл settings.py
Этот файл содержит базовый URL для UI тестов:
BASE_URL = "https://www.kinopoisk.ru/s/"

### Файл config.py
Этот файл содержит настройки для API тестов:
BASE_URL = "https://api.kinopoisk.dev/v1.4"
HEADERS = {
    "accept": "application/json",
    "X-API-KEY": "XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX"
}
Убедитесь, что данные настройки корректны перед запуском тестов. Для получения "X-API-KEY" воспользуйтесь информацией с сайта https://api.kinopoisk.dev/documentation. 

## Запуск тестов
### API Тесты
Для запуска тестов API используйте команду:
pytest -v --alluredir=allure-results test_api.py

### UI Тесты
Для запуска тестов UI используйте команду:
pytest -v --alluredir=allure-results test_ui.py

### Просмотр отчетов Allure
Чтобы сгенерировать и просмотреть отчеты Allure после выполнения тестов, выполните следующие шаги:

1. Генерация отчета:
   allure serve allure-results
2. После выполнения команды откроется браузер с подробным отчетом.

## Детальное описание тестов
### API Тесты (test_api.py)
test_api_responses: Проверяет статус-коды различных API эндпоинтов.
test_search_content_by_id: Проверяет поиск контента по ID.
test_search_content_by_title: Проверяет поиск контента по названию фильма.
test_search_person_by_name: Проверяет поиск актеров и режиссеров по имени.
test_search_content_invalid_params: Проверяет обработку неверных параметров запроса.
test_search_content_id_out_of_bounds: Проверяет обработку запроса с недопустимым значением ID.
Каждый тест в API покрыт Allure шагами для лучшего понимания процесса тестирования.

### UI Тесты (test_ui.py)
test_search_by_year: Проверяет поиск контента по году выпуска.
test_search_by_title: Проверяет поиск контента по названию фильма.
test_search_by_genre: Проверяет поиск контента по жанру.
test_search_by_actor: Проверяет поиск контента по названию фильма и имени актера.
test_search_by_country: Проверяет поиск контента по стране.

Модуль search_page.py
Этот модуль реализует Page Object Model для страницы поиска, что позволяет легко и удобно взаимодействовать с элементами UI.

Примеры методов:

search_by_year: Вводит год и инициирует поиск.
search_by_title: Вводит название фильма и инициирует поиск.
search_by_genre: Выбирает жанр и инициирует поиск.
search_by_actor: Вводит название фильма и имя актера, затем инициирует поиск.
search_by_country: Выбирает страну и инициирует поиск.
Для ожидания элементов используются методы:

wait_for_element: Ожидает видимости элемента на странице.
wait_for_element_with_text: Ожидает появления текста в элементе.

## Полезные советы
Page Object Model: Рекомендуется изучить этот паттерн, так как он упрощает работу с тестами и делает их более устойчивыми.
Allure: Инструмент для создания подробных отчетов о выполненных тестах. Полезен для анализа ошибок и улучшения тестов.
Параметризация: Использование параметризации позволяет покрыть больше сценариев меньшим количеством кода.

## Заключение
Этот проект обеспечивает полный набор тестов для API и UI приложения Кинопоиск. Его легко расширить и адаптировать под нужды вашего проекта. Автоматизация тестов поможет вам быстрее находить и исправлять ошибки, улучшая качество вашего продукта.


