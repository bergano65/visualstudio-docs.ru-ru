---
title: Учебник по DOCKER. часть 7. Использование Docker Compose
description: Описывает установку и использование Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 81f70612b05920ea58c752a878831f1d6de34098
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176796"
---
# <a name="use-docker-compose"></a>Использование Docker Compose

[DOCKER Compose](https://docs.docker.com/compose/) — это средство, разработанное для помощи в определении и совместном использовании приложений с несколькими контейнерами. С помощью функции составления можно создать файл YAML для определения служб и с помощью одной команды, что позволяет прокрутить все вверх или разорвать их.

*Большое* преимущество использования функции создания состоит в том, что вы можете определить стек приложения в файле, удержать его в корне репозитория проекта (теперь управление версиями) и легко предоставить другому пользователю возможность участвовать в работе над проектом. Кому-то нужно клонировать репозиторий и начать создание приложения. На самом деле вы можете увидеть несколько проектов в GitHub/GitLab, выполняющих именно эту возможность.

Итак, как начать?

## <a name="install-docker-compose"></a>Установка Docker Compose

Если вы установили DOCKER Desktop для Windows или Mac, у вас уже есть Docker Compose! Экземпляры Play-with-DOCKER уже имеют Docker Compose также установлены. Если вы используете компьютер под управлением Linux, вам потребуется установить Docker Compose с помощью приведенных [здесь инструкций](https://docs.docker.com/compose/install/).

После установки вы сможете запустить следующий пример и просмотреть сведения о версии.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Создание файла создания

1. В корне проекта приложения создайте файл с именем `docker-compose.yml` .

1. В файле компоновки мы начнем с определения версии схемы. В большинстве случаев лучше использовать последнюю поддерживаемую версию. Можно просмотреть [ссылку на создание файла](https://docs.docker.com/compose/compose-file/) для текущих версий схемы и таблицу совместимости.

    ```yaml
    version: "3.7"
    ```

1. Затем определите список служб (или контейнеров), которые требуется использовать как часть приложения.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Теперь вы начнете перенос службы за раз в файл создания.

## <a name="define-the-app-service"></a>Определение службы приложений

Помните, что это была команда, используемая для определения контейнера приложения (замените ` \ ` символы `` ` `` в в Windows PowerShell).

```bash
docker run -dp 3000:3000 \
  -w /app -v ${PWD}:/app \
  --network todo-app \
  -e MYSQL_HOST=mysql \
  -e MYSQL_USER=root \
  -e MYSQL_PASSWORD=secret \
  -e MYSQL_DB=todos \
  node:12-alpine \
  sh -c "yarn install && yarn run dev"
```

1. Сначала определите запись службы и изображение для контейнера. Можно выбрать любое имя для службы. Имя будет автоматически преобразовано в сетевой псевдоним, что будет полезно при определении службы MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Как правило, команда будет близка к `image` определению, хотя при упорядочении нет необходимости. Итак, переместите его в файл.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Перенесите `-p 3000:3000` часть команды, определив `ports` для нее службу. Здесь вы будете использовать [короткий синтаксис](https://docs.docker.com/compose/compose-file/#short-syntax-1) , но также доступен более подробный [длинный синтаксис](https://docs.docker.com/compose/compose-file/#long-syntax-1) .

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Затем перенесите рабочий каталог ( `-w /app` ) и сопоставление томов ( `-v ${PWD}:/app` ) с помощью `working_dir` `volumes` определений и. Тома также имеют [короткий](https://docs.docker.com/compose/compose-file/#short-syntax-3) и [длинный](https://docs.docker.com/compose/compose-file/#long-syntax-3) синтаксис.

   Одним из преимуществ Docker Compose определений томов является использование относительных путей из текущего каталога.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Наконец, перенесите определения переменных среды с помощью `environment` ключа.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Определение службы MySQL

Теперь пора определить службу MySQL. Для этого контейнера использовалась следующая команда (замените ` \ ` символы `` ` `` в в Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Сначала определите новую службу и назовите ее, `mysql` чтобы она автоматически выдает псевдоним сети. Укажите также образ, который будет использоваться.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Затем определите сопоставление томов. При запуске контейнера с `docker run` именем именованный том был создан автоматически. Однако это не происходит при выполнении с созданием. Необходимо определить том в разделе верхнего уровня `volumes:` , а затем указать точку подключения в конфигурации службы. Просто указав только имя тома, используются параметры по умолчанию. Однако [доступно множество других вариантов](https://docs.docker.com/compose/compose-file/#volume-configuration-reference) .

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Наконец, необходимо указать только переменные среды.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

На этом этапе полный `docker-compose.yml` вид должен выглядеть следующим образом:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Запуск стека приложений

Теперь, когда у вас есть `docker-compose.yml` файл, его можно запустить.

1. Во-первых, убедитесь, что никакие другие копии приложения и базы данных не выполняются ( `docker ps` и `docker rm -f <ids>` ).

1. Запустите стек приложений с помощью `docker-compose up` команды. Добавьте `-d` флаг для выполнения всех операций в фоновом режиме. Кроме того, можно щелкнуть правой кнопкой мыши файл создания и выбрать параметр **создать** для боковой панели VS Code. 

    ```bash
    docker-compose up -d
    ```

    При выполнении этого действия вы увидите следующий результат:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Вы заметите, что том был создан и в сети! По умолчанию Docker Compose автоматически создает сеть специально для стека приложений (поэтому вы не определили его в файле создания).

1. Просмотрите журналы с помощью `docker-compose logs -f` команды. Вы увидите журналы каждой из служб, которые чередуются в один поток. Это чрезвычайно полезно, когда необходимо отслеживать проблемы, связанные с временем. В этом случае в `-f` журнале появится следующий флаг, так как он будет выдавать выходные данные в режиме реального времени по мере его создания.

    Если вы еще не сделали этого, вы увидите выходные данные следующего вида:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Имя службы отображается в начале строки (часто окрашено), чтобы облегчить различение сообщений. Если вы хотите просмотреть журналы для определенной службы, можно добавить имя службы в конец команды Logs (например, `docker-compose logs -f app` ).

    > [!TIP]
    > **Ожидание базы данных перед запуском приложения** Когда приложение запускается, оно фактически находится в состоянии ожидания и готово к подключению, прежде чем пытаться подключиться к it.DocКер не имеет встроенной поддержки для ожидания завершения, запуска и подготовки другого контейнера перед запуском другого контейнера. Для проектов на основе узлов можно использовать зависимость [ожидания порта](https://github.com/dwmkerr/wait-port) . Аналогичные проекты существуют для других языков и платформ.

1. На этом этапе вы сможете открыть приложение и увидеть его выполнение. И Эй! Вы не работаете с одной командой!

## <a name="see-the-app-stack-in-the-docker-extension"></a>См. раздел стек приложений в расширении DOCKER.

Если взглянуть на расширение DOCKER, можно изменить параметры группирования, используя "шестеренки" и "Group By". В этом случае необходимо просмотреть контейнеры, сгруппированные по имени проекта:

![Расширение VS с созданием](media/vs-app-project-collapsed.png)

Если вы твирл сеть, вы увидите два контейнера, которые вы определили в файле создания.

![Расширение VS с расширенным созданием](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Разорвать все

Когда все будет готово к завершению работы, просто запустите `docker-compose down` или щелкните правой кнопкой мыши приложение в списке контейнеров в VS Code расширения DOCKER и выберите пункт **Создание**и удаление. Контейнеры будут прекращаться, а сеть будет удалена.

> [!WARNING]
> **Удаление томов** По умолчанию именованные тома в файле создания не удаляются при запуске `docker-compose down` . Если вы хотите удалить тома, необходимо добавить `--volumes` флаг.

После отключения можно переключиться на другой проект, запустить `docker-compose up` и подготовиться к работе с этим проектом. На самом деле это не намного проще!

## <a name="recap"></a>Резюме

В этом разделе вы узнали о Docker Compose и о том, как она помогает значительно упростить определение и совместное использование приложений с несколькими службами. Вы создали файл создания, переведя команды в соответствующий формат создания.

На этом этапе вы начинаете заключить учебник. Тем не менее, существует несколько рекомендаций по созданию образа, так как существует большая проблема с Dockerfile, которую вы используете. Итак, давайте посмотрим!

## <a name="next-steps"></a>Дальнейшие действия

Продолжайте работу с руководством.

> [!div class="nextstepaction"]
> [Рекомендации по созданию образов](image-building-best-practices.md)
