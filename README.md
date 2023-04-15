# О ресурсе

![](docs/assets/hero-bg.jpg)

Репозиторий проекта [propwashservice.ru](https://propwashservice.ru)

Данные материалы исходят из личного опыта, наблюдений в FPV сообществе. Никакой рекламы, спонсорства, все по личной инициативе для продвижения хобби в массы. Приятного чтения!

Проект базируется на генераторе [VitePress](https://vitepress.vuejs.org) и [Github Pages](https://pages.github.com/)

Содержимое страниц лежит в папке `docs`. Pull request'ы по улучшению ресурса приветствуются.

## Локальный запуск и отладка

### С помощью yarn

```shell
yarn install
yarn dev
```

### С помощью Docker
1. Запустить докер контейнер
    ```bash
    docker compose -f docker/compose.local.yaml up -d --build
    ```
    > Данная команда соберёт образ и запустит контейнер
1. [Перейти на http://localhost:5173](http://localhost:5173). Проверить, что всё запустилось
1. Открыть свою любимую IDE и редактировать файлы в папке `docs/`
    > Ваши изменения должны моментально отображаться в браузере
1. По окончании работы остановить контейнер
    ```bash
    docker compose -f docker/compose.local.yaml stop
    ```
1. Или даже удалить контейнер, образ и сеть (докер создаёт сеть по умолчанию, ему это нужно для работы)
    ```bash
    docker compose -f docker/compose.local.yaml down --rmi all --volumes --remove-orphans
    ```

Примечание: только изменени файлов в папке `docs/` изменения будут отображаться в браузере моментально. При изменении других файлов (доустановили библиотеку, отредактировали конфигурацию, ...) необходимо пересобрать образ и перезапустить контейнер.

### Авторы

- Валентина, Михаил - команда [PropWash Service](https://github.com/ikherty)
- Андрей Щ. - [EIIIE](https://github.com/EIIIE)
- Дмитрий В. - [dimazollo](https://github.com/dimazollo)
- Никита - [Suput](https://github.com/Suput)
