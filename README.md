# SPA Веб-приложение для управления расписанием доступа

## Описание

Это веб-приложение позволяет пользователям авторизоваться с помощью email и пароля, редактировать расписание для каждого дня недели, а также проверять доступность по времени.

**Особенности**:
- Авторизация с использованием JWT.
- Использование Redux для управления состоянием.
- Валидация форм с использованием Formik и Yup.
- Хранение данных в MongoDB с Mongoose.
- API для проверки времени доступа.
- Защита от CSRF и XSS.
- Индикация доступных и недоступных временных интервалов.

## Технологии

- **Frontend**:
    - React.js
    - Redux
    - Formik, Yup
    - Tailwind CSS
    - date-fns

- **Backend**:
    - Node.js
    - Express.js (или NestJS)
    - JWT для авторизации
    - MongoDB, Mongoose
    - class-validator

- **Безопасность**:
    - Защита от CSRF и XSS
    - Капча для критичных операций (например, изменение расписания)

## Установка и запуск проекта

### 1. Клонирование репозитория

Сначала клонируйте репозиторий на ваш локальный компьютер:

```bash
git clone https://github.com/lxsmlv/schedule-guard.git
cd schedule-guard
```

### 2. Установка зависимостей

Перейдите в соответствующие директории и установите зависимости.

Для фронтенда:
```bash
cd frontend
npm install
```

Для бэкенда:
```bash
cd backend
npm install
```

### 3. Запуск приложения

Для фронтенда:
```bash
npm start
```

Для бэкенда:
```bash
npm run dev
```

После этого приложение будет доступно по адресу http://localhost:3000 в вашем браузере.

## Основные функции приложения

### Авторизация
- Приложение поддерживает авторизацию через email и пароль.
- Разрешенные пользователи:
  - user1@some.com (пароль: user1@some.com)
  - user2@some.com (пароль: user2@some.com)
- После успешной авторизации пользователь получает JWT для дальнейших запросов.

### Управление расписанием
- На главной странице отображается таблица с 7 днями недели.
- Каждый день недели имеет временные интервалы (например, Понедельник: 00:00-24:00).
- Авторизованный пользователь может редактировать время для каждого дня недели.

### API для проверки времени доступа
- Эндпоинт на сервере проверяет текущее время и день недели и возвращает успешный ответ, если время находится в разрешенном интервале, или ошибку, если оно вне интервала.

### Безопасность
- В приложении реализована защита от CSRF и XSS.
- Для критичных операций (например, изменение расписания) добавлена защита через капчу или подтверждение через email.

### UI/UX
- Для отображения расписания используется таблица с возможностью редактирования временных интервалов.
- Интервалы, которые доступны в текущий момент, подсвечиваются цветом для улучшения UX.

## Структура проекта

### Frontend

- **Авторизация:**
  - Форма авторизации с полями email и пароля.
  - Проверка логина (user1@some.com, user2@some.com) и пароля (тот же как и логин).
  - После авторизации пользователь получает JWT для дальнейших запросов.

- **Управление расписанием:**
    - Отображение таблицы с 7 днями недели и временными интервалами.
    - Возможность редактировать время для каждого дня.

- **Индикация доступности:**
    - Визуальное выделение доступных и недоступных временных интервалов с использованием цветов.

### Backend

- **Авторизация:**
    - Реализован эндпоинт для авторизации пользователей и генерации JWT токена.

- **API для проверки времени доступа:**
    - Эндпоинт, проверяющий текущее время в зависимости от дня недели и возвращающий успешный или неуспешный ответ.

- **Защита:**
    - Реализована защита от CSRF и XSS.
    - Капча для критичных операций.

### База данных
- MongoDB используется для хранения данных о пользователях и расписаниях.
- Mongoose используется для работы с базой данных.

## Лицензия

- MIT