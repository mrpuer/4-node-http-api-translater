# Создаем собственный переводчик, используя модуль http

* `npm start` then go to [http://localhost:3000] (http://localhost:3000) in browser.

Существует сервис Яндекс.Переводчик, у него есть [хорошо описанное API](https://tech.yandex.ru/translate/).

1.  Необходимо реализовать собственный сервис, который будет слушать порт 3000.
2.  На GET-запрос будет отдавать HTML-форму, в которую пользователь будет вводить текст и по кнопке отправлять эти данные на сервер с помощью POST-запроса.
3.  Отправить запрос к [https://translate.yandex.net/api/v1.5/tr.json/translate](https://translate.yandex.net/api/v1.5/tr.json/translate) c параметрами:
    *   `key` — ключ, который вам предстоит самостоятельно получить с [сервера яндекса](https://tech.yandex.ru/translate/), либо же можно воспользоваться этим ключом: `trnsl.1.1.20160723T183155Z.f2a3339517e26a3c.d86d2dc91f2e374351379bb3fe371985273278df`;
    *   `text` — непосредственно текст из формы;
    *   `lang` — описание языка перевода, на ваше усмотрение.
4.  Ответ от сервиса Яндекса показать пользователю в браузере в любом виде.

### Пример:

Запрос:

`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20160723T183155Z.f2a3339517e26a3c.d86d2dc91f2e374351379bb3fe371985273278df&text=подосиновик&lang=ru-en`

Ответ:

    {
      "code": 200,
      "lang": "ru-en",
      "text": [
          "boletus"
      ]
    }

Сервис необходимо реализовать на языке Node.js. Допускается использование **только встроенных модулей (http)**.