
# Laravel Sail Production Environment

Этот один из вариантов организации окружения для существующих приложений на фреймворке [Laravel](https://laravel.com/docs/10.x/installation) с пакетом [Sail](https://laravel.com/docs/10.x/sail), который подходит для разработки и эксплуатации в `production`.

В окружении:
* PHP-FPM `8.2` с пользователем `sail`, процессы тоже запускаются от этого пользователя
* Nginx `1.21.6`
* MySQL `8` с созданием базы данных `test`

> Перед разворачиванием необходимо создать `.env` с нужными значениями, пример в `.env.example`.

Для инициализации нового приложения нужно [следовать документации Sail](https://laravel.com/docs/10.x/installation#docker-installation-using-sail), а затем можно взять конфигурацию из репозитория. Либо инициализировать новый проект на новом окружении из репозитория:
```bash
# поднимаем инфраструктуру
$ docker compose up -d

# создаем проект
$ docker compose exec -u "$(id -u):$(id -g)" php composer create-project laravel/laravel example-app

# перемещаем содержимое директории example-app в корень
$ docker compose exec -u "$(id -u):$(id -g)" php mv ./example-app/* .

# все что не переместилось из директории example-app перемещаем в корень руками, совмещая файлы
```

Для инициализации существующего приложения с представленным окружением достаточно:
```bash
$ docker compose run --rm -u "$(id -u):$(id -g)" php composer install
```
