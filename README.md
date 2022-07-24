# screener

Скрипт, работающий в фоне. Мониторит нажатие клавиши (например колесико мышки) 
и отсылает скрин экрана в telegram.

## Быстрый запуск
Готовый `.exe` можно найти в папке `builds`. Там лежат все сборки со инструкциями по использованию.

## Как работает

- Скрипт, отсылает скрин экрана в чат телеграм через бота по нажатию на колесико мыши.
- Скрипт использует конфиг в виде `config.json` файла, который обязательно должен 
лежать в одной папке со скриптом, со след. полями:
    - max_time - (int) максимальное время работы скрипта в минутах
    - bot_token - (str) токен бота (в формате 0000000:aaaaaaa...)
    - chat_id - (str) id чата в телеграмме (может быть отрицательным)
    - exit_btn_code - (int) - код клавишы выхода, изначально TAB (9) 
    [примеры клавиш](https://stackoverflow.com/questions/31363860/how-do-i-get-the-name-of-a-key-in-pywin32-giving-its-keycode)
    
## Как настроить телеграм бота
- Создать бота
    - Написать в телеграмме боту `@BotFather`: `/newbot`
    - Ввести имя нового бота
    - Ввести логин нового бота
    - Получить от `@BotFather` его токен
- Создать чат (не канал) и добавить в него бота
- Узнать id чата: 
    - Добавить в созданный чат `@chatid_echo_bot` или `@get_my_chat_id_bot`, он сразу напечатает id чата, сразу после его можно удалить из беседы.
    - Либо вставить в url строку в браузере `https://api.telegram.org/bot<TOKEN>/getUpdates`, нажать enter, в полученном результате найти "chat"->"id"

**!!! После изменения кол-ва участников чата chat_id может изменится** 

## Дополнительно
Исполняемый файл (.exe) можно запустить прямо с флешки не загружая его 
на рабочий стол. Вставив флешку нужно запустить файл, подождать около 10 секнд 
на загрзку программы в оперативную память и запуск. После это проверить, что 
скрины отправляются и вынуть флешку.


## Как собрать .exe файл для windows (для разработки новых версий)
- устронавить pyinstaller
    ```
    pip install pyinstaller
    ```
- собрать .exe файл
    ```
    pynistaller main.py -F -w
    ```
    - флаг F  - чтобы приложение собрась в один файл
    - флаг w - говорит о том, что приложение оконное (не будет создаваться терминал при запуске)
