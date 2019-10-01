---
title: Модульное тестирование контейнерного приложения
author: ghogen
description: Выполняйте модульные тесты для каждой сборки проекта Docker в Visual Studio
ms.author: ghogen
ms.date: 06/17/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: ec5aea44362cf82f6745671cc0706f80e01a60ad
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "71125971"
---
# <a name="how-to-run-unit-tests-for-a-containerized-app"></a>Практическое руководство. Выполнение модульных тестов для контейнерного приложения

Модульные тесты можно выполнять для каждой сборки контейнерного проекта, изменив файл Dockerfile.

## <a name="prerequisites"></a>Предварительные требования

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- Установка [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)
- Настройка модульных тестов для выполнения с помощью команды [dotnet test](/dotnet/core/tools/dotnet-test)
- Установка [расширения окна "Контейнеры"](https://aka.ms/vscontainerspreview)

## <a name="add-unit-tests-to-the-dockerfile"></a>Добавление модульных тестов в Dockerfile

Перед изменением файла Dockerfile среда Visual Studio производит оптимизацию производительности. При сборке в конфигурации **отладки** Visual Studio выполняет сборку проектов на локальном компьютере, а затем копирует результаты в контейнер. Поэтому выполняется только первый этап многоэтапной сборки, определенной в файле Dockerfile. Дополнительные сведения см. в статье [Процесс сборки с помощью инструментов Visual Studio для работы с контейнерами](container-build.md).

Чтобы добавить модульные тесты в многоэтапный файл Dockerfile, добавьте этап `unit-test` в Dockerfile между этапами `build` и `publish`.

```
FROM build AS unit-test
RUN dotnet unit-test --logger:trx
```

В конфигурации **отладки** Visual Studio выполняет только первый этап, поэтому этап `unit-test` выполняется только в конфигурации **выпуска**. Но даже в конфигурации **выпуска** результаты журнала не будут включаться в окончательный образ, так как его сборка выполняется на этапе `base`, а не на этапе `unit-test`. Чтобы запустить тесты и создать образ, в котором можно просмотреть журналы, используйте следующую команду:

```cmd
docker build --target:unit-test
```

## <a name="next-steps"></a>Следующие шаги

Далее можно просмотреть журналы тестирования в [окне "Контейнеры"](view-and-diagnose-containers.md) (если установлено соответствующее расширение).  

Чтобы просмотреть журналы тестирования, нажмите клавиши **CTRL**+**Q** и выполните поиск по запросу **Контейнеры**, чтобы открыть окно **Контейнеры**. В окне **Контейнеры** найдите контейнер, откройте вкладку **Файлы**, найдите файл с результатами тестов (TRX) в файловой системе контейнера и откройте его, чтобы просмотреть результаты в Visual Studio.

