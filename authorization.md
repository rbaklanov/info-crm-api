# Авторизация
Авторизация осуществляется по протоколу OAuth 2.0. Подробная документация по протоколу: [RFC 6749](http://tools.ietf.org/html/rfc6749).
Зарегистрированное приложение(пользователь) может запрашивать у Info-CRM данные без получения и хранения его логина и пароля.

### Инсталляция OAuth2 на сервере Info-CRM
Предварительно необходимо установить на сервере [Laravel Passport](https://laravel.com/docs/5.3/passport#installation)
и создать password client для последующей авторизации через Oauth2 сервер:
```PHP
php artisan passport:client --password
 
What should we name the password grant client? [ Password Grant Client]:
> InfoGroup Mobile Manager App            

Password grant client created successfully.
Client ID: 6
Client Secret: OJCTCTD3Duwuw89X2rQvf8AaN48bNRyeSwIgEoKj
```
Client ID и Client Secret понадобятся для авторизации. В дальнейшем будут обозначаться как```client_id``` и ```client_secret```.
