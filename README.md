# Telegram bot 
Бот создан на языке C++, что гарантирует высокую скорость работы и надежность.

С помощью кроссплатформенного фреймворка vcpkg нужно установить две библиотеки:**tgbot**, **SQLiteCpp**; и провести интеграцию с IDE MS Visual Studio.
Я выбрал SQLite, потому что эта база данных может работать без подключения на сервере.
Далее нам нужно в боте BotFather нам нужно создать токен бота, по которому мы соединяем серверную и клиентские части нашего проекта.

### Серверная часть:
В программе есть бесконечный цикл, который мы запускаем после сборки проекта. Он работает до тех пор, пока мы не остановим программу. Цикл фиксирует сообщения пользователей и нажатия кнопок и передаёт их в обработчик команд или кнопок соответственно. Бот может обработать команды: /start /id /functions /game /exit. В начале программы создается 3 клавиатуры с кнопками. Первая клавиатура может выполнять следующие функции при нажатии кнопок: выводить информацию об авторе, правила пользования ботом, функции бота, помощь при использовании бота и связь с хозяином бота в телеграмме: добавлена ссылка на него в url кнопки. Вторая клавиатура позволяет вывести chat-id пользователя и начать игру. Третья клавиатура содержит только кнопку exit для выхода из игры. 

**Использование базы данных:**

При первом нажатии пользователем функции /start его chat-id(уникальный номер пользователя) записывается в нашу базу данных, в которую добавлены два поля: id и idTg. Первый нумерует пользователей по порядку(от 1 и так далее), а второе поле содержит chat-id каждого пользователя. Если пользователь уже пользовался возможностями чат-бота, то он уже не добавится повторно в базу данных, в серверной части в консоли будет выведено: (номер айди...) found . Таким образом, я могу следить за тем, сколько пользователей пользуется моим ботом. Также, каждое действие, которое делает пользователь, отображается в консоли серверной части с его номером айди.

---

### Клиентская часть:
Клиентская часть бота - это то, что видят и с чем взаимодействуют пользователи в Telegram.
**Стартовое сообщение:** При запуске бота, пользователь получает приветственное сообщение с описанием его возможностей и ссылкой на помощь (/help или /functions). 

**Клавиатуры:**
     **Главная клавиатура:**
         Кнопка "Author": Выводит информацию о создателе.
         Кнопка "Rules": Выводит информацию правилах использования, функциях бота.
         Кнопка "Help": Выводит функции, которые исполняет бот.
         Кнопка "Functions": Описывает возможности бота, такие как получение ID, игра "Угадай число" и т.д.
         Кнопка "Contact": Предоставляет ссылку чат с создателем бота.
     **Вторая клавиатура:**
         Кнопка "ID": Выводит chat-id пользователя.
         Кнопка "Игра": Запускает игру "Угадай число".
     **Третья клавиатура:**
         Кнопка "Выход": Выводит сообщение о выходе из игры, удаляет клавиатуру.

---

### Функции бота:

- *Выдает ID пользователя. Просто отправь команду /id, и бот мгновенно покажет тебе свой уникальный идентификатор.*
- *Игра "Угадай число". Бот загадывает число, а тебе предстоит угадать его! Играя в эту простую, но захватывающую игру, ты сможешь проверить свою интуицию и логику.*

### Удобный интерфейс:

- *Простые кнопки: Используй кнопки для выбора команд и управления игрой.* 
- *Интуитивное управление: Бот разработан с учетом простоты и удобства использования.*











