# Telegram Drova Session Manager Bot

Это скрипт на языке Python для Telegram-бота, который взаимодействует с API Drova. Бот позволяет владельцам станций просматривать свои последние игровые сессии, а также устанавливать свой X-Auth-Token для доступа к API.

Поддержать авторов: [Xerz](https://qiwi.com/n/XRZVS) и [dreamer2](https://qiwi.com/n/DREAMER2) 

## Требования

Подтверждена работоспособность с `python 3.9.1` и `python-telegram-bot==13.7`

## Запуск

1. Склонируйте этот репозиторий на свой локальный компьютер.
2. Скачайте базы данных IP адресов `GeoLite2` (файлы называется `GeoLite2-City.mmdb` и `GeoLite2-ASN.mmdb`) в папку с репозиторием.
3. Установите необходимые пакеты Python (см. импорты в файле бота)
3. Создайте нового бота в Telegram, следуя инструкциям [BotFather](https://core.telegram.org/bots#6-botfather).
4. Далее, в зависимости от вашей ОС
   
### Linux/MacOS
6. Как только вы получите токен своего бота, установите его как переменную среды в вашем терминале с помощью следующей команды:
```bash
export TELEGRAM_BOT_TOKEN=<ваш токен бота>
```
7. Запустите бота, выполнив команду `python bot.py` в вашем терминале.

### Windows

(спасибо dreamer2)

6. Замените `REPLACE-TO-YOUR-TELEGRAM-BOT-TOKEN` в файле `startbot.cmd` на ваш токен
7. Запустите `startbot.cmd`.

###
## Доступные команды
1. ```/token ваш_токен_здесь```

Установите свой X-Auth-Token, отправив эту команду боту. Токен можно получить на странице "Мои сервера", считав QR-код для авторизации в мобильном приложении. **Внимание! Токен даёт доступ к вашему аккаунту!** Не отправляйте токен своего аккаунта в непроверенные боты!

2.  ```/removetoken```

Используется для удаления вашего токена из базы бота если вы не планируете дальше его использовать.

3.  ```/station```

Используйте эту команду, чтобы получить список ваших станций и выбрать станцию для показа сессий. Вы также можете указать ID станции, чтобы получить сессии для конкретной станции, например `/station id_станции_здесь`.

4. ```/sessions```

Используйте эту команду, чтобы получить список сессий для указанной станции. Чтобы обновить список сессий, просто нажмите кнопку "Update" внизу сообщения. Чтобы показать только сессии длинее пяти минут, используйте команду `/sessions short`

5. ```/limit число_здесь```

Используйте команду, чтобы сменить количество выводимых сессий. По умолчанию 5.

6. ```/dumpall```

Используйте команду  для получения последних 1000 сессий (ограничение API) каждой станции в виде `csv` файла

7. ```/dumponefile```

Используйте команду  для получения последних 1000 сессий (ограничение API) каждой станции в виде одного `xlsx` файла

8. ```/current``` (спасибо dreamer2)

Используйте команду для получения краткого списка станций и последних сессий на каждой станции (имена станций имеют следующую разметку - ~~выключенные~~, *неопубликованные*, в ожидании, **с активной сессией**)

9. ```/disabled```

Выводит по станциям список отключенных игр.

10. ```/stationsInfo```

Выводит список станций с их адресами.

11. ```/dumpStationsProducts``` 

Экспортирует в файл список станций и что на них установлено.

12. ```/dumpStationsProductsWithTime```

Экспортирует в файл список станций и что на них установлено со временем.

13. ```/dumpstationsproductsmonth```

Экспортирует в файл список станций и что на них установлено со временем за месяц.

###
## Для удобства использования в описании бота через BotFather можно прописать меню команд

пишете ему /setcommands , выбираете своего бота и вставляете список команд, например такой
```
token - 123-456-789 установить токен из qr кода личного кабинета мерчанта
removetoken - удалить токен пользователя из бота
current - Краткий список последних сессий по всем станциям
disabled - Список отключенного на станции
station - [id станции] выбор станции из списка или ручным вводом её id
stationsinfo - Список станций с их адресами
limit - N смена ограничения на вывод сессий
sessions - [short] просмотр сессий со всех или с выбранной станции
dumpall - экспорт сессий по серверам
dumponefile - экспорт сессий одним файлом
dumpstationsproducts - экспорт списка установленного на станциях
dumpstationsproductswithtime - экспорт списка установленного на станциях со временем
dumpstationsproductsmonth - экспорт списка установленного на станциях со временем за месяц
```

## TODO

- Перевод станций в частный режим из опубликованного и обратно
- Отдельная команда для короткого списка сессий
- Общая отказоустойчивость и обработка ошибок в частности
- Уведомления
  - об отключенных играх
- Определение города и провайдера клиента и расстояния от станции до него
