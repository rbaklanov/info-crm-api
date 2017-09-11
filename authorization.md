# Авторизация
Авторизация осуществляется по протоколу OAuth 2.0. Подробная документация по протоколу: [RFC 6749](http://tools.ietf.org/html/rfc6749).
Зарегистрированное приложение(пользователь) может запрашивать у Info-CRM данные без получения и хранения его логина и пароля.

## Инсталляция OAuth2 на сервере Info-CRM
Предварительно необходимо установить на сервере [Laravel Passport](https://laravel.com/docs/5.3/passport#installation)
и создать password client для последующей авторизации через Oauth2 сервер:
```
php artisan passport:client --password
 
What should we name the password grant client? [ Password Grant Client]:
> InfoGroup Mobile Manager App            

Password grant client created successfully.
Client ID: 6
Client Secret: OJCTCTD3Duwuw89X2rQvf8AaN48bNRyeSwIgEoKj
```
Client ID и Client Secret понадобятся для авторизации. В дальнейшем будут обозначаться как ```CLIENT_ID``` и ```CLIENT_SECRET```.

## Получение авторизации
```POST http://infogroup.online/oauth/token```

```PHP
grant_type: 'password',
client_id: CLIENT_ID,
client_secret: CLIENT_SECRET,
username: USER_LOGIN,
password: USER_PASSWORD,
scope: '*'
```

### Ответ
Успешный ответ приходит с кодом ```200 OK``` и содержит тело:

```
token_type: "Bearer",
expires_in: 31535999,
access_token:  "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImRlZmExMDQ0MGI3NDE2YWU3ZjIzNjk5M2Y2ZmUyZDgxN2MzNDYxZDc4OGYxNmU4MWQyZjE1MGFmZGE5ZWYwZWVkZmQ0NWZjYmUwMGU5MjJlIn0.eyJhdWQiOiI2IiwianRpIjoiZGVmYTEwNDQwYjc0MTZhZTdmMjM2OTkzZjZmZTJkODE3YzM0NjFkNzg4ZjE2ZTgxZDJmMTUwYWZkYTllZjBlZWRmZDQ1ZmNiZTAwZTkyMmUiLCJpYXQiOjE0OTM4MzkwNTAsIm5iZiI6MTQ5MzgzOTA1MCwiZXhwIjoxNTI1Mzc1MDQ5LCJzdWIiOiIyIiwic2NvcGVzIjpbIioiXX0.LOcNpAWKciywwUPdzNEhflN2JgYLV-Nad5VNNVMqasXgPR8s1BzI0dh0d_pRetINbKv_b1ueAd0tV3tZGo_Rg7IwEcGjovxCi6jfGWTA3zxc3naT2dG3tneR-uzMI-puGl9UUUXNjKUYIgtMLymCyHnlPs4kQllHIW1tbF4nDmUnbPwhxq2mIy891gZJmDu6FnBA48As5dOnxVLSoX-4yvA852gzcmLFr7gTfsSVc-IR-HwkZlhSgdbxcyG_u2yB4GKBL9eJ7tC4ZAvSGilsM7xOR5uUoS-JNmgGBX8xMf_SzLvH7C0KOa_Nnvem2Iy7PVgoQV135Ie1H-ODQN2CSPSWjbtB9M2j3NJSTl2IXXRwqpLqlUJ1TAZMAa71ZECyXvrgUSlJ2tVVTvrJ5X_7E_KM1sTUkiBGrQmSXsjWepb4hEdM2F4JjDlgTSAxeyX6xZoHdt0Intc7ymDVU5dHmj_-3dDr8J4yVVKXeBNWpsJbn-NFc9zo6hsVLWTX_TB9UgCxK-l9P68CNpV5JlD_lWeosfwHczuQJzJa_ui_2j4jKJiQ9F2Z3f5krXq9q_6S8jj5RK8bUF3eAw2tybhKrEnQAp4vkQHZTBB5O4GBASo59WjZpM_IMZyHKlpx8SGasvxd0FsoPdSMqTNT4ZHUkHtePAcG7yRBz6ZWRIMFqX8",
refresh_token:  "GjuX/urxcbKqpeWviiIFaL2CHAKLWhiwwSwsWmfMjR3aOZUq8bOfTiHnpzOhPJ9K2hVwfnlnq66XaCgjmT41b2IroNSZ0fIn+FPuW7hUd2eSLOo/oo347C4cz5vu6P3fAopoWhpKQ7w25txj2XIKxj8jOOSwkTTemoYpJRbpR+EwHa3wGIOgCNR46/oAusElwR5/fXo8sjECskvoUOEclaSzJsbSS+qqW8A3Wz3SW/WaXNix2fUjMUheQbkQ9TiZNHWXEgFTkiawwONhXW2RVwPJzl4lh08iYJ9iBB6cayGU8DE3ibBR2IrszeMvrW354XcLgG8M6RpBEP7iN3WzAKgLNf+x1biInoZUpfor4hcWtgqbrHbdDWoDrXk0VbK55WWzkdM+c20xhMpfguTBX8gMwt1x4o1743y/lF8GhlfKV4iIPL8omAjmey9nKs2PJAZoxAz0iJ8LD7OLsL3qdXkNladEGsovzSt+TZMvPBbUmgAH69VGIj4Htc99ftwz0hmVmYHYdnGEeNi87haOzSblDHX6rht2xLDHBu6NIG+cjfOKSzx9Rhy+UxycKut1BnoTVineBd7LNdS2QIKp5Am9gscQuGVRvD++tN17GmbIr0rf8waFTQ6WdClYkGU2vFWbfLXG0uDxQ89Xo3wCgBShtLiz1r896KkeAJirEJ8="
```

```access_token``` нужно сохранить и передавать вместе со всеми запросами к API в заголовке ```Authorization``` (далее по тексту упоминается как ```ACCESS_TOKEN```)
