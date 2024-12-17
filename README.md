# Перенос резервной копии портала Bitrix
## Этап 1

1. Переходим на портале битрикса в раздел `Рабочий стол` → `Настройки` → `Инструменты` → `Резервное копирование` → `Создание резервной копии`
2. Выбираем `Размещение резервной копии: в папке сайта`
3. Переходим в раздел `Параметры`
4. Настраиваем параметры копии согласно снимку
![Uploading Снимок экрана 2024-12-17 в 14.18.40.png…]()
5. Дожидаемся успешного резервирования

---
## Этап 2
1. Заходим на тестовый портал удаляем из публичной директории абслютно все
2. Переносим зарезервированные архивы с одного поратала на другой (использовать `shell` соединение)

---
## Этап 3
1. Подключаемся по ssh к порталу, на котороый переносим
2. Выполняем следующи команды
```
mysql
```
```
show databases;
```
```
SELECT * FROM mysql.user;
```
```
DROP DATABASE sitemanager;
```
```
CREATE DATABASE sitemanager CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```
```
CREATE USER 'bitrix1221'@'localhost' IDENTIFIED BY 'qwerty123';
```
```
GRANT ALL PRIVILEGES ON sitemanager.* TO 'bitrix1221'@'localhost';
```
```
FLUSH PRIVILEGES;
```

---
## Этап 4
1. Переходим на [сайт](https://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=32&LESSON_ID=2014)
2. Оттуда скачиваем [файл](https://www.1c-bitrix.ru/download/scripts/restore.php)
3. Помещаем в корень локальных папок дев портала
4. Переходим по ссылке `https://www.you_portal_bx/restore.php`








