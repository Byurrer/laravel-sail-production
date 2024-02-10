
# Laravel Sail Production Environment

Этот один из вариантов организации окружения для существующих приложений на фреймворке [Laravel](https://laravel.com/docs/10.x/installation) с пакетом [Sail](https://laravel.com/docs/10.x/sail), который подходит для разработки и эксплуатации в `production`.

В окружении:
* PHP-FPM 8.2 с пользователем `sail`, процессы тоже запускаются от этого пользователя
* Nginx 1.21.6
* MySQL 8 с созданием базы данных `test`

> Перед разворачиванием необходимо создать `.env` с нужными значениями, пример в `.env.example`.

Для инициализации существующего приложения с представленным окружением достаточно:
```bash
$ docker compose run --rm -u "$(id -u):$(id -g)" php composer install
```
