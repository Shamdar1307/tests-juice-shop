# Проект: Функциональное тестирование формы регистрации OWASP Juice Shop

## Описание

Функциональное тестирование формы регистрации и API тестирование веб-приложения OWASP Juice Shop.
Проверены позитивные и негативные сценарии валидации email, пароля и поля подтверждения, а также API-эндпоинты через Postman.

## Артефакты

- UI тест-кейсы — /test-cases/registration (30 шт.)
- API тест-кейсы — /test-cases/API (6 шт.)
- Баг-репорты — /bug-reports (3 шт.)
- Чек-листы — /checklists (UI и API)
- Postman коллекция — /tools/Postman (JSON)
- Результаты прогона — Test result.txt

## Результаты

- UI    | Тест-кейсы : 30 | Пройдено : 27 | Дефекты : 3 |
- API   | Тест-кейсы :  6 | Пройдено :  6 | Дефекты : 0 |
- Итого | Тест-кейсы : 36 | Пройдено : 33 | Дефекты : 3 |

  **Пройденные проверки UI**  
- Email: валидный, с точкой/плюсом/спецсимволами, заглавные буквы  
- Пароль: 5–40 символов, сложный, без цифр/букв/спецсимволов  
- Негатив: пустые поля, короткий/длинный пароль, несовпадение паролей

  **Пройденные проверки Smoke API** 6/6 тестов пройдено
- Регистрация пользователя
- Авторизация и получение токена
- Добавление товара в корзину
- Просмотр корзины
- Оформление заказа
- История заказов

  **Найденные дефекты**  
- BUG-001 — регистрация с email из 5 символов (t@m.r)  
- BUG-002 — регистрация с email без домена верхнего уровня (test@mail)  
- BUG-003 — регистрация возможна после изменения пароля, когда пароли уже не совпадают

## Ссылки

- [Google Sheets (чек-лист, тест-кейсы, баг-репорты)](https://docs.google.com/spreadsheets/d/1_ptnI1aRQtayL6JIFpdTAUxo1SjAMcxWN9nBkuZ9ogo/edit?usp=sharing)
- Стенд: [OWASP Juice Shop](https://github.com/juice-shop/juice-shop) v20.0.0 (Docker)
- Окружение: Windows 11, Яндекс.Браузер

## Запуск стенда
- docker pull bkimminich/juice-shop
- docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop

## Postman Smoke-тест

- Коллекция Postman для API тестирования Juice Shop. tools/Postman/OWASP JuiceShop.postman_collection.json
- Окружения Postman tools/Postman/Smoke-user-environment.postman_environment.json
- Сценарий: Регистрация → Логин → Добавление в корзину → Оформление → История заказов
- Результат: 6/6 тестов пройдено
- Запуск: 1) docker run --rm -p 127.0.0.1:3000:3000 bkimminich/juice-shop
	  2) Import коллекции в Postman
	  3) Run (Smoke-user)