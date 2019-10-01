---
title: Свойства сборки с помощью инструментов Visual Studio для работы с контейнерами
author: ghogen
description: Обзор процесса сборки с помощью инструментов для работы с контейнерами
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4bc6cb4221d85bd43b98b2ac36c34c919937960b
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "71126061"
---
# <a name="container-tools-build-properties"></a>Свойства сборки с помощью инструментов для работы с контейнерами

Вы можете настроить способ сборки контейнерных проектов в Visual Studio, задав свойства, используемые MSBuild для сборки проекта. Например, можно изменить имя файла Dockerfile, указать теги и метки для образов, предоставить дополнительные аргументы, передаваемые в команды Docker, и указать, должна ли среда Visual Studio выполнять определенные оптимизации производительности, например производить сборку за пределами среда контейнеров. Кроме того, можно задать свойства отладки, такие как имя запускаемого исполняемого файла, и аргументы командной строки.

Чтобы задать значение свойства, измените файл проекта. Например, допустим, что файл Dockerfile имеет имя *MyDockerfile*. Задать свойство `DockerfileFile` в файле проекта можно указанным ниже образом.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Вы можете добавить значение свойства в существующий элемент `PropertyGroup` или, если его нет, создать новый элемент `PropertyGroup`.

В таблице ниже приводятся свойства MSBuild, доступные для контейнерных проектов.

| Имя свойства | ОПИСАНИЕ | Значение по умолчанию  |
|---------------|-------------|----------------|
| DockerfileFile | Описывает файл Dockerfile по умолчанию, который будет использоваться для сборки или запуска контейнера проекта. Значение также может быть путем. | Dockerfile |
| DockerfileTag | Тег, который будет использоваться при сборке образа Docker. При отладке к тегу добавляется строка ":dev". | Имя сборки после удаления символов, отличных от букв и цифр, строится по следующим правилам. <br/> Если итоговый тег состоит только из цифр, добавляется префикс "image" (например, image2314). <br/> Если итоговый тег является пустой строкой, используется тег "image". |
| DockerContext | Контекст по умолчанию, используемый при сборке образа Docker. | Задается средой Visual Studio. |
| ContainerDevelopmentMode | Определяет, включена ли оптимизация "сборка в узле" (отладка в быстром режиме).  Допустимые значения: **Fast** и **Regular**. | Быстрый |
| DockerDefaultTargetOS | Целевая операционная система по умолчанию, используемая при сборке образа Docker. | Задается средой Visual Studio. |
| DockerImageLabels | Набор меток по умолчанию, применяемых к образу Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |
| ContainerVsDbgPath | Путь к отладчику VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |
| DockerfileBuildArguments | Дополнительные аргументы, передаваемые в команду сборки Docker. | Неприменимо. |
| DockerfileRunArguments | Дополнительные аргументы, передаваемые в команду запуска Docker. | Неприменимо. |
| DockerfileRunEnvironmentFiles | Разделенный точками с запятой список файлов среды, применяемых во время запуска Docker. | Неприменимо. |
| DockerfileFastModeStage | Этап Dockerfile (то есть целевой объект), который будет использоваться при сборке образа в режиме отладки. | Первый этап в файле Dockerfile (base) |
| DockerDebuggeeProgram | При отладке отладчик должен запустить этот исполняемый файл. | Для проектов .NET Core : dotnet; для проектов ASP.NET .NET Framework: неприменимо (всегда используется IIS) |
| DockerDebuggeeArguments | При отладке отладчик должен передать эти аргументы в запущенный исполняемый файл. | Неприменимо к проектам ASP.NET .NET Framework |
| DockerDebuggeeWorkingDirectory | При отладке отладчик должен использовать этот путь в качестве рабочего каталога. | C:\app (Windows) или /app (Linux) |
| DockerDebuggeeKillProgram | Эта команда используется для завершения выполняющегося процесса в контейнере. | Неприменимо к проектам ASP.NET .NET Framework |

## <a name="next-steps"></a>Следующие шаги

Общие сведения о свойствах MSBuild см. в статье [Свойства MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>См. также

[Свойства сборки Docker Compose](docker-compose-properties.md)

[Параметры запуска инструментов для работы с контейнерами](container-launch-settings.md)

[Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
