Описание

В 2018 году Джеймс Клир написал Atomic Habits, 
книгу о новых полезных привычках и преодолении старых вредных привычек. 
Разработанная платформа позволяет создавать собственные привычки и 
делиться ими с другими пользователями. 
Пользователи также будут получать напоминания в telegram о 
необходимости завершить привычку вовремя.

Требования

Python

Redis

PostgreSQL

Настройте свои личные настройки

Создайте .env конфигурационный файл с вашими личными настройками в корневом каталоге 
проекта, согласно образцу, указанному в .env.sample. 
Заполните файл в соответствии со своими личными данными.

Подготовить

1. Запустите сервис Redis;
    
2. Создайте базу данных в postgresql. Имя базы данных должно совпадать с именем, указанным в файле;
 
3. Перенесите свою базу данных с помощью команды: python manage.py migrate;

4. Создайте telegram-бота для отправки информации и вставьте токен в .env файл.

Выполняется

Чтобы запустить проект, введите celery -A config beat -l info -S django команду в терминале.
Откройте второе окно терминала и введите celery -A config worker -l INFO (добавить eventlet для Windows).
Необходимо отслеживать и выполнять фоновые задачи.
Откройте новое окно терминала и запустите python manage.py runserver.
Проект готов к использованию!

Работа с API (пользователями)

http://127.0.0.1:8000/users/registration/ - регистрация пользователя

http://127.0.0.1:8000/users/list/ - показать всех пользователей

http://127.0.0.1:8000/users/detail/int:pk/ - показывать подробную информацию о пользователе

http://127.0.0.1:8000/users/update/int:pk/ - обновить информацию о пользователе

http://127.0.0.1:8000/users/delete/int:pk/ - удалить информацию о пользователе

http://127.0.0.1:8000/users/token/ - получить токен для пользователя

http://127.0.0.1:8000/users/token/refresh/ - обновить токен пользователя

Работа с API (привычки)

http://localhost:8000/habits/create/ - создать привычку

http://localhost:8000/habits/list/ - показывать все привычки пользователя

http://localhost:8000/habits/detail/int:pk/ - показывать подробную информацию о привычках пользователя

http://127.0.0.1:8000/habits/update/int:pk/ - обновить привычку

http://127.0.0.1:8000/habits/delete/int:pk/ - удалить привычку

http://127.0.0.1:8000/habits/public_list/ - показывать все публичные привычки

Описание запросов

Модель пользователя

электронная почта - используйте свой адрес электронной почты для регистрации на платформе

имя_пользователя telegram - необходимое условие для получения напоминаний от telegram-бота 
(указывать без дополнительных символов перед ником)

пароль - введите свой пароль, не забудьте ввести его, чтобы получить токен

password2 - дублировать пароль при регистрации пользователя для повторной верификации

Модель привычки

место - место вашей привычки

время выполнения привычки

действие - что делать

награда - то, что вы получите за свою не приятную привычку

is_pleasant - флажок для обозначения приятной или не очень привычки

link_pleasant - неприятная привычка может иметь приятную привычку (в данном случае без награды)

частота - по умолчанию ежедневно, но вы можете проверить день недели (понедельник-воскресенье)

продолжительность - продолжительность действия привычки (менее 120 минут)

is_public - флаг для публичной или частной привычки

