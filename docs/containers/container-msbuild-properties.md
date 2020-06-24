---
title: Свойства сборки с помощью инструментов Visual Studio для работы с контейнерами
author: ghogen
description: Обзор процесса сборки с помощью инструментов для работы с контейнерами
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 427a70d9bc4f6ef326ffb16e7d26df9d8fae2365
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283207"
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

В таблице ниже приводятся свойства MSBuild, доступные для контейнерных проектов. Версия пакета NuGet применяется к [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Имя свойства | Описание | Значение по умолчанию  | Версия пакета NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Определяет, включена ли оптимизация "сборка в узле" (отладка в быстром режиме).  Допустимые значения: **Fast** и **Regular**. | Быстрый |1.0.1872750 или более поздняя|
| ContainerVsDbgPath | Путь к отладчику VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 или более поздняя|
| DockerDebuggeeArguments | При отладке отладчик должен передать эти аргументы в запущенный исполняемый файл. | Неприменимо к проектам ASP.NET .NET Framework |1.7.8 или более поздняя|
| DockerDebuggeeProgram | При отладке отладчик должен запустить этот исполняемый файл. | Для проектов .NET Core : dotnet; для проектов ASP.NET .NET Framework: неприменимо (всегда используется IIS) |1.7.8 или более поздняя|
| DockerDebuggeeKillProgram | Эта команда используется для завершения выполняющегося процесса в контейнере. | Неприменимо к проектам ASP.NET .NET Framework |1.7.8 или более поздняя|
| DockerDebuggeeWorkingDirectory | При отладке отладчик должен использовать этот путь в качестве рабочего каталога. | C:\app (Windows) или /app (Linux) |1.7.8 или более поздняя|
| DockerDefaultTargetOS | Целевая операционная система по умолчанию, используемая при сборке образа Docker. | Задается средой Visual Studio. |1.0.1985401 или более поздняя|
| DockerImageLabels | Набор меток по умолчанию, применяемых к образу Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 или более поздняя|
| DockerFastModeProjectMountDirectory|В **быстром режиме** это свойство управляет тем, где выходной каталог проекта подключен к тому в выполняющемся контейнере.|C:\app (Windows) или /app (Linux)|1.9.2 более поздней версии|
| DockerfileBuildArguments | Дополнительные аргументы, передаваемые в команду [сборки Docker](https://docs.docker.com/engine/reference/commandline/build/). | Не применяется |1.0.1872750 или более поздняя|
| DockerfileContext | Контекст по умолчанию, используемый при сборке образа Docker в качестве пути относительно Dockerfile. | Задается средой Visual Studio. |1.0.1872750 или более поздняя|
| DockerfileFastModeStage | Этап Dockerfile (то есть целевой объект), который будет использоваться при сборке образа в режиме отладки. | Первый этап в файле Dockerfile (base) |
| DockerfileFile | Описывает файл Dockerfile по умолчанию, который будет использоваться для сборки или запуска контейнера проекта. Значение также может быть путем. | Dockerfile |1.0.1872750 или более поздняя|
| DockerfileRunArguments | Дополнительные аргументы, передаваемые в команду [запуска Docker](https://docs.docker.com/engine/reference/commandline/run/). | Не применяется |1.0.1872750 или более поздняя|
| DockerfileRunEnvironmentFiles | Разделенный точками с запятой список файлов среды, применяемых во время запуска Docker. | Не применяется |1.0.1872750 или более поздняя|
| DockerfileTag | Тег, который будет использоваться при сборке образа Docker. При отладке к тегу добавляется строка ":dev". | Имя сборки после удаления символов, отличных от букв и цифр, строится по следующим правилам. <br/> Если итоговый тег состоит только из цифр, добавляется префикс "image" (например, image2314). <br/> Если итоговый тег является пустой строкой, используется тег "image". |1.0.1872750 или более поздняя|

## <a name="example"></a>Пример

В следующем файле проекта показаны примеры некоторых из этих параметров.

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>Следующие шаги

Общие сведения о свойствах MSBuild см. в статье [Свойства MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>См. также

[Свойства сборки Docker Compose](docker-compose-properties.md)

[Параметры запуска инструментов для работы с контейнерами](container-launch-settings.md)

[Зарезервированные и стандартные свойства MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
