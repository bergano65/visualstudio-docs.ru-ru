---
title: Учебник по DOCKER. часть 8. размещение изображений
description: Изучение и управление слоями изображений в образах DOCKER.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176820"
---
# <a name="image-layering"></a>Раскрытие изображений

Знаете ли вы, что создаете образ? С помощью `docker image history` команды можно увидеть команду, которая использовалась для создания каждого слоя в изображении.

1. Используйте `docker image history` команду, чтобы просмотреть слои в `getting-started` изображении, созданном ранее в этом учебнике.

    ```bash
    docker image history getting-started
    ```

    Вы должны получить выходные данные, которые выглядят примерно так (даты и идентификаторы могут отличаться).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Каждая из строк представляет слой в изображении. Здесь показана основа в нижней части с новым слоем вверху. С помощью этого можно также быстро увидеть размер каждого слоя, помогая диагностировать крупные образы.

1. Обратите внимание, что несколько строк усекаются. При добавлении `--no-trunc` флага вы получите полный вывод (да, для получения неусеченных выходных данных используется усеченный флаг).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Кэширование слоев

Теперь, когда вы видели слой в действии, есть важное занятие, которое поможет сократить время сборки для образов контейнеров.

> После изменения слоя все нижестоящие слои также необходимо создать заново.

Давайте взглянем на Dockerfile, который использовался еще раз...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Вернувшись к выходному журналу образа, вы увидите, что каждая команда в Dockerfile превращается в новый слой в изображении. Возможно, вы помните, что при внесении изменений в образ необходимо переустановить зависимости Yarn. Есть ли способ исправить это? Не имеет смысла поставлять одни и те же зависимости при каждой сборке, верно?

Чтобы устранить эту проблему, можно изменить структуру Dockerfile, чтобы обеспечить поддержку кэширования зависимостей. Для приложений на основе узлов эти зависимости определяются в `package.json` файле. Итак, что если сначала скопировать только этот файл, установить зависимости, а *затем* скопировать все остальное? После этого повторное создание зависимостей Yarn выполняется только в случае изменения `package.json` . Имеет смысл?

1. Обновите Dockerfile, чтобы скопировать в `package.json` первую очередь, установите зависимости, а затем скопируйте все остальное в.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Создайте новый образ с помощью `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Вы должны увидеть результат, подобный этому...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Вы увидите, что все слои были перестроены. Отлично, так как вы изменили Dockerfile, очень немного.

1. Теперь внесите изменения в `src/static/index.html` файл (например, измените на, например, на `<title>` "приложение Awesome TODO").

1. Создайте образ DOCKER сейчас с помощью `docker build` . На этот раз выходные данные должны выглядеть немного иначе.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    В первую очередь следует заметить, что сборка выполнялась гораздо быстрее! Вы увидите, что у всех шагов 1-4 есть `Using cache` . Итак, радостных! Вы используете кэш сборки. Отправка и извлечение этого образа и обновлений в нем будет выполняться гораздо быстрее. Радостных!

## <a name="multi-stage-builds"></a>Многоэтапные сборки

Хотя мы не будем углубляться в этот учебник, в этом руководстве многоэтапные сборки являются невероятно мощным средством, помогающим использовать несколько этапов для создания образа. Для них существует несколько преимуществ.

- Отдельные зависимости времени сборки от зависимостей среды выполнения
- Сократите общий размер образа, добавив *только* то, что требуется для работы приложения

### <a name="maventomcat-example"></a>Пример Maven/Tomcat

При создании приложений на основе Java требуется JDK для компиляции исходного кода в байт-код Java. Однако это JDK не требуется в рабочей среде. Кроме того, вы можете использовать такие средства, как Maven или Gradle, для помощи в построении приложения.
Они также не нужны в окончательном образе. Справка по многоэтапным сборкам.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

В этом примере используется один этап (вызываемый `build` ) для выполнения фактической сборки Java с помощью Maven. Второй этап (начиная с `FROM tomcat` ) копирует в файлы с `build` этапа. Окончательный образ — только последний создаваемый этап (который можно переопределить с помощью `--target` флага).

### <a name="react-example"></a>Пример реагирования

При создании приложений, реагирующих на реагирование, требуется среда узла для компиляции кода JS (обычно JSX), таблиц стилей Sasser и др. в статический HTML, JS и CSS. Если вы не выполняете отрисовку на стороне сервера, вам даже не нужна среда узла для рабочей сборки. Почему не следует поставлять статические ресурсы в статическом контейнере nginx?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Здесь вы используете `node:12` образ для выполнения сборки (максимизация кэширования слоя) и последующего копирования выходных данных в контейнер nginx. Здорово, правда?

## <a name="recap"></a>Резюме

Понимая немного усилий относительно структурирования изображений, можно быстрее создавать изображения и доставлять меньше изменений. Многоэтапные сборки также позволяют сократить общий размер образа и повысить уровень безопасности контейнера, разделив зависимости времени сборки от зависимостей среды выполнения.

## <a name="next-steps"></a>Дальнейшие действия

Продолжайте работу с руководством.

> [!div class="nextstepaction"]
> [Развертывание в облаке](deploy-to-cloud.md)