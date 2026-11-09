HOMO GHOSTUS NEWS — редакция с паролем

Содержимое:
- public/index.html — публичная главная страница и лента статей
- public/redaktsiya/index.html — закрытая панель редактора
- netlify/functions/api.mjs — API с проверкой сессии
- Netlify Blobs — хранение опубликованных статей

ВАЖНО: для работы редакции нужен deploy через Git-репозиторий с включёнными Netlify Functions. Простая загрузка HTML через Netlify Drop не разворачивает Functions.

ПУБЛИКАЦИЯ:
1. Распаковать архив.
2. Загрузить ВСЕ файлы и папки в новый GitHub-репозиторий (или заменить файлы в репозитории, уже подключённом к Netlify).
3. В Netlify подключить репозиторий: Add new project → Import an existing project → выбрать репозиторий.
4. Build command оставить пустой; Publish directory: public. Функции лежат в netlify/functions.
5. В Netlify: Project configuration → Environment variables → Add a variable:
   ADMIN_PASSWORD = придуманный длинный уникальный пароль редакции
   SESSION_SECRET = длинная случайная строка (не менее 32 символов)
   Не публикуйте и никому не отправляйте эти значения. Не вставляйте их в HTML или GitHub.
6. После добавления переменных заново запустить deploy.
7. Открыть https://ВАШ-ДОМЕН/redaktsiya/ и войти.
8. Новые статьи появляются на главной в блоке «Последние публикации».

ПЕРЕНОС НА ТЕКУЩИЙ САЙТ:
Если текущий Netlify-сайт подключён к Git, добавьте файлы из архива в тот же репозиторий, сохранив структуру папок. Проверьте настройки Build/Publish. Если сайт опубликован только через ручную загрузку папки, сначала подключите Git-репозиторий.

Безопасность:
- Пароль хранится только в Netlify Environment Variables.
- Cookie сессии HttpOnly, Secure, SameSite=Strict, срок 8 часов.
- Не используйте тот же пароль, что от почты или других аккаунтов.
- Не размещайте SESSION_SECRET или ADMIN_PASSWORD в публичном репозитории.
