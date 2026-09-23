
1. Набір автоматизованих тестів для Ringotel Web.

Використовується:
- Java
- Selenium WebDriver
- TestNG
- Gradle
- WebDriverManager

Тести працюють з Ringotel Web:
https://app.shell.ringotel.co/login


2. ЩО ПЕРЕВІРЯЄТЬСЯ

На цей момент автоматизовані такі сценарії:

- Login користувачів
- Створення контакту
- Пошук створеного контакту
- Відправлення повідомлень
- Перевірка доступності messaging для контактів
- Видалення чатів
- Зміна Presence status
- Вихідні та вхідні дзвінки
- Answer / Reject
- Hold / Resume
- Mute / Unmute
- Start / Stop Recording
- More Call Actions
- Call Transfer
- Blind Transfer
- Attended Transfer
- Завершення дзвінка


3. ЩО ПОТРІБНО ДЛЯ ЗАПУСКУ

Потрібно:

- Java
- Google Chrome, Mozilla Firefox або Microsoft Edge
- скачаний проєкт



4. ШВИДКИЙ ЗАПУСК ЧЕРЕЗ CMD

1. Скачати або клонувати репозиторій.
2. Відкрити кореневу папку проєкту — там, де знаходиться `build.gradle`.
3. У цій папці відкрити CMD / Terminal.
4. Виконати потрібну команду.

Запуск усіх тестів:

gradlew.bat test

За замовчуванням використовується Chrome.


Запуск усіх тестів у Firefox:

gradlew.bat test -Pbrowser=firefox


Запуск усіх тестів у Edge:

gradlew.bat test -Pbrowser=edge


Запуск у Chrome:

gradlew.bat test -Pbrowser=chrome


Якщо `gradlew.bat` у репозиторії відсутній, але Gradle встановлений у системі:

gradle test


5. ЗАПУСК ОКРЕМОГО TEST CLASS ЧЕРЕЗ CMD

Приклад:

gradlew.bat test --tests "ringotel.tests.LoginTests"

Інші приклади:

gradlew.bat test --tests "ringotel.tests.PresenceTests"

gradlew.bat test --tests "ringotel.tests.CallTests"

gradlew.bat test --tests "ringotel.tests.CallControlsTests"


З іншим браузером:

gradlew.bat test --tests "ringotel.tests.CallTests" -Pbrowser=firefox


6. ЗАПУСК ОДНОГО КОНКРЕТНОГО TEST METHOD ЧЕРЕЗ CMD

Формат:

gradlew.bat test --tests "package.ClassName.methodName"


Приклад:

gradlew.bat test --tests "ringotel.tests.PresenceTests.changePresenceStatuses"


Ще один приклад:

gradlew.bat test --tests "ringotel.tests.CallControlsTests.rejectIncomingCall"


З Firefox:

gradlew.bat test --tests "ringotel.tests.CallControlsTests.rejectIncomingCall" -Pbrowser=firefox


7. ДОДАТКОВІ GRADLE TASKS

У `build.gradle` є окремі tasks:

QA:

gradlew.bat qa


Quick suite:

gradlew.bat quick

Використовує:

src/test/resources/quick.xml


Regression suite:

gradlew.bat regr

Використовує:

src/test/resources/regression.xml


Приклади з іншим браузером:

gradlew.bat quick -Pbrowser=firefox

gradlew.bat regr -Pbrowser=edge


8. ЗАПУСК ЧЕРЕЗ INTELLIJ IDEA

Тести також можна запускати без CMD.

Запуск одного test method:

1. Відкрити потрібний test class.
2. Знайти метод з `@Test`.
3. Натиснути зелений Run біля методу.


Запуск усього test class:

1. Відкрити потрібний class.
2. Натиснути Run біля назви class.


Запуск усіх тестів:

1. Відкрити пакет `ringotel.tests`.
2. Натиснути правою кнопкою.
3. Вибрати Run tests.


9. ПІДТРИМУВАНІ БРАУЗЕРИ

Підтримуються:

chrome
firefox
edge

Якщо браузер не переданий у команді, використовується Chrome.

Для вибору браузера через CMD використовується:

-Pbrowser=chrome

або:

-Pbrowser=firefox

або:

-Pbrowser=edge


10. TEST USERS

Тестова organization:

Domain:
testwebsoftphone


User 1:

Username:
4321

Password:
obFxbmYKYy9pwjAD


User 2:

Username:
1234

Password:
R0eE6jAMUmyck7uD


11. ЯКІ TEST CLASSES Є В ПРОЄКТІ

LoginTests
- перевірка Login для тестових користувачів


PresenceTests
- перевірка зміни Presence status:
  - Busy
  - At the Desk
  - Online


ContactTests
- створення нового Contact
- пошук створеного Contact


ChatTests
- відкриття Contact
- відправлення Message
- перевірка відправленого Message
- перевірка Messaging для imported contact


ContactMessagingAuditTests
- перевірка доступності Messaging для контактів
- відправлення test message
- видалення створених chat після перевірки


ChatCleanupTests
- видалення всіх chat у тестового користувача


CallTests
- дзвінок 4321 -> 1234
- дзвінок 1234 -> 4321
- Answer
- Active Call
- завершення дзвінка


CallControlsTests
- Incoming Call
- Answer
- Reject
- Hold
- Resume
- Mute
- Unmute
- Start Recording
- Stop Recording
- More Call Actions
- Video action
- Device action
- Add Party
- Transcript
- Call Transfer
- Blind Transfer
- Attended Transfer
- завершення дзвінка


12. SCREENSHOTS ПРИ ПОМИЛЦІ

Якщо test падає, автоматично створюється screenshot.

Screenshots зберігаються у папці:

screenshots

Приклад імені:

screen-1780000000000.png


13. ЛОГИ І РЕЗУЛЬТАТИ

Gradle показує:

- passed
- failed
- skipped

Також у console виводяться додаткові logs із тестів.

Для failed test показується повний exception.


14. ВАЖЛИВО ПЕРЕД ЗАПУСКОМ

Тести виконують реальні дії в test Ringotel environment.

Вони можуть:

- створювати Contacts
- відправляти Messages
- видаляти Chats
- змінювати Presence
- здійснювати Calls
- Reject Calls
- запускати Call Recording

Особливо обережно запускати:

ChatCleanupTests

оскільки цей test видаляє всі chats тестового користувача.


15. КОРОТКО — НАЙЧАСТІШІ КОМАНДИ

Усі тести:

gradlew.bat test


Усі тести у Firefox:

gradlew.bat test -Pbrowser=firefox


Усі тести у Edge:

gradlew.bat test -Pbrowser=edge


QA:

gradlew.bat qa


Quick:

gradlew.bat quick


Regression:

gradlew.bat regr


Один class:

gradlew.bat test --tests "ringotel.tests.CallTests"


Один method:

gradlew.bat test --tests "ringotel.tests.CallControlsTests.rejectIncomingCall"
"""

