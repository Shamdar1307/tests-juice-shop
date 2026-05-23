# Проект: Функциональное тестирование формы регистрации OWASP Juice Shop

## Описание

Ручное тестирование формы регистрации веб-приложения OWASP Juice Shop.  
Проверены позитивные и негативные сценарии валидации email, пароля и поля подтверждения.

## Артефакты

- Тест-кейсы — /test-cases
- Баг-репорты — /bug-reports
- Чек-лист — Checklist.txt
- Результаты прогона — Test result.txt
- Postman коллекции — /tools

## Результаты

| Всего тест-кейсов : 30 | Пройдено : 27 | Дефекты : 03 |

  **Пройденные проверки**  
- Email: валидный, с точкой/плюсом/спецсимволами, заглавные буквы  
- Пароль: 5–40 символов, сложный, без цифр/букв/спецсимволов  
- Негатив: пустые поля, короткий/длинный пароль, несовпадение паролей

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