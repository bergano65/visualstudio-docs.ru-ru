---
title: Компиляция и сборка кода TypeScript с использованием NuGet
description: Узнайте, как добавить поддержку Typescript в проекты Visual Studio с помощью пакета NuGet.
ms.date: 7/23/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 375f56d8a367c6d5cb090e10069b714b5a3843f2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969546"
---
# <a name="compile-typescript-code-aspnet-core"></a>Компиляция кода TypeScript (ASP.NET Core)

Вы можете добавить в проекты поддержку TypeScript, используя пакет TypeScript SDK, который доступен по умолчанию в Visual Studio Installer или в виде пакета NuGet. Для проектов, которые разработаны в Visual Studio 2019, рекомендуется использовать пакеты NuGet TypeScript. Они обеспечивают лучшую переносимость между разными средами и платформами.

Для проектов ASP.NET Core чаще всего пакеты NuGet используются для компиляции TypeScript с помощью .NET Core CLI. Пока файл проекта не будет вручную изменен для импорта целевых объектов сборки из установки TypeScript SDK, пакет NuGet останется единственным способом включения компиляции TypeScript с помощью команд .NET Core CLI, таких как `dotnet build` и `dotnet publish`. Кроме того, для [интеграции MSBuild](https://www.staging-typescript.org/docs/handbook/compiler-options-in-msbuild.html) с ASP.NET Core и TypeScript следует выбрать пакет NuGet, а не пакет npm.

## <a name="add-typescript-support-with-nuget"></a>Добавление поддержки TypeScript с использованием NuGet

[Пакет NuGet TypeScript](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild) позволяет включить поддержку TypeScript. Когда в проект устанавливается пакет NuGet или TypeScript 3.2 или более новой версии, в редактор загружается соответствующая версия языковой службы TypeScript.

Если среда Visual Studio установлена, файл node.exe, который входит в комплект, в ней будет выбран автоматически. Если у вас не установлена среда Node.js, мы рекомендуем установить версию LTS с веб-сайта [Node.js](https://nodejs.org/en/download/).

1. В Visual Studio откройте проект ASP.NET Core.

1. Выбор в обозревателе решений Щелкните правой кнопкой узел проекта и выберите **Управление пакетами NuGet**. На вкладке **Обзор** найдите **Microsoft.TypeScript.MSBuild**, а затем нажмите кнопку **Установить** справа, чтобы установить пакет.

   ![Добавление пакета NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio добавляет пакет NuGet в раздел **Зависимости** узла в обозревателе решений. Следующая ссылка на пакет добавляется в файл *.csproj.

   ```xml
   <PackageReference Include="Microsoft.TypeScript.MSBuild" Version="3.9.7">
      <PrivateAssets>all</PrivateAssets>
      <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
   </PackageReference>
   ```

1. Щелкните правой кнопкой мыши узел проекта и выберите **Добавить > Новый элемент**. Выберите **Файл конфигурации TypeScript JSON**, а затем нажмите кнопку **Добавить**.

   Visual Studio добавит файл *tsconfig.json* в корневую папку проекта. Этот файл можно использовать для [настройки параметров](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) компилятора TypeScript.

1. Откройте файл *tsconfig.json* и обновите его, задав необходимые параметры компилятора.

   Ниже приведен пример простого файла *tsconfig.json*.

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   В этом примере:
   - *include* указывает компилятору, где искать файлы TypeScript (*.ts).
   - Параметр *outDir* указывает выходную папку для обычных файлов JavaScript, которые преобразуются компилятором TypeScript.
   - Параметр *sourceMap* указывает, нужно ли компилятору создать файлы *sourceMap*.

   В приведенной выше конфигурации представлен пример базовой конфигурации TypeScript. Сведения о других параметрах см. в разделе о файле [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

### <a name="build-the-application"></a>Построение приложения

1. В проект добавьте файлы TypeScript ( *.ts*) или TypeScript JSX ( *.tsx*), а затем добавьте код TypeScript. В качестве простого примера TypeScript используйте следующий код:

   ```typescript
   let message: string = 'Hello World';
   console.log(message);
   ```

1. Если вы используете старую версию проекта не на основе SDK, перед сборкой выполните инструкции из раздела [Удаление файлов, импортированных по умолчанию](#remove-default-imports).

1. Выберите **Сборка > Собрать решение**.

   Хотя сборка приложения выполняется автоматически при его запуске, рассмотрим, что происходит в процессе сборки.

   Если вы создали сопоставители с исходным кодом, откройте папку, указанную в параметре *outDir*, где вы найдете созданные файлы *.js с файлами *js.map.

   Файлы сопоставителя с исходным кодом необходимы для отладки.

1. Чтобы компиляция выполнялась каждый раз при сохранении проекта, задайте параметр *compileOnSave* в файле *.tsconfig.

   ```json
   ```{
      "compileOnSave":  true,
      "compilerOptions": {
      }
   }
   ```

Пример использования gulp с запускателем задач для сборки приложения см. в разделе о [ASP.NET Core и TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html).

Если возникнут проблемы, из-за которых Visual Studio будет использовать для Node.js или стороннего средства не ту версию, возможно, потребуется задать путь для использования в Visual Studio. Выберите **Средства** > **Параметры**. В разделе **Проекты и решения** выберите **Управление веб-пакетами** > **Внешние веб-инструменты**.

### <a name="run-the-application"></a>Выполнение приложения

Инструкции по запуску приложения после его компиляции см. в разделе [Создание первого приложения Node.js](/visualstudio/ide/quickstart-nodejs?toc=%2Fvisualstudio%2Fjavascript%2Ftoc.json#run-the-application).

### <a name="nuget-package-structure-details"></a>Сведения о структуре пакета NuGet

`Microsoft.TypeScript.MSBuild.nupkg` содержит две основные папки:

- Папка *build*.

    Эта папка содержит два файла.
    Оба файла представляют собой точки входа: для основного целевого файла TypeScript и файла .props соответственно.

    1. *Microsoft.TypeScript.MSBuild.targets*.

        В этом файле указываются переменные, определяющие платформу среды выполнения, например путь к *TypeScript.Tasks.dll*, перед импортом *Microsoft.TypeScript.targets* из папки *tools*.

    2. *Microsoft.TypeScript.MSBuild.props*.

        Этот файл используется для импорта *Microsoft.TypeScript.Default.props* из папки *tools* и определения свойств, указывающих на то, что сборка инициирована с помощью NuGet.

- Папка *tools*.

    В пакетах версий до 2.3 содержится только папка tsc. На корневом уровне расположены файлы *Microsoft.TypeScript.targets* и *TypeScript.Tasks.dll*.

    В пакетах версии 2.3 и выше на корневом уровне расположены файлы `Microsoft.TypeScript.targets` и `Microsoft.TypeScript.Default.props`. Дополнительные сведения об этих файлах см. в разделе о [конфигурации MSBuild](https://www.typescriptlang.org/docs/handbook/compiler-options-in-msbuild.html).

    Кроме того, в папке содержатся три вложенные папки:

    1. *net45.*

        Эта папка содержит библиотеку `TypeScript.Tasks.dll` и другие библиотеки DLL, от которых она зависит.
        Если проект создается на платформе Windows, MSBuild использует библиотеки DLL из этой папки.

    2. *netstandard1.3.*

        Эта папка содержит другую версию `TypeScript.Tasks.dll`, которая используется при создании проектов на компьютере с ОС, отличающейся от Windows.

    3. *tsc.*

        Эта папка содержит `tsc.js`, `tsserver.js` и все файлы зависимостей, которые нужно запускать в качестве скриптов узла.

        > [!NOTE]
        > Если среда Visual Studio установлена, файл *node.exe*, который входит в комплект, будет выбран автоматически. В противном случае вам нужно будет установить Node.js на компьютере.

        В версиях до 3.1 содержался исполняемый файл `tsc.exe` для запуска компиляции. В версии 3.1 вместо него используется `node.exe`.

### <a name="remove-default-imports"></a>Удаление файлов, импортированных по умолчанию

В старых проектах ASP.NET Core, где используется [формат не в стиле SDK](https://docs.microsoft.com/nuget/resources/check-project-format), может потребоваться удалить некоторые элементы файла проекта.

Если вы используете пакет NuGet для поддержки MSBuild в проекте, файл проекта не должен импортировать `Microsoft.TypeScript.Default.props` или `Microsoft.TypeScript.targets`. Файлы импортируются пакетом NuGet, поэтому их отдельное включение может привести к непредвиденным последствиям.

1. Щелкните проект правой кнопкой мыши и выберите пункт **Выгрузить проект**.

1. Щелкните проект правой кнопкой мыши и выберите команду **Изменить \<*project file name*\>** .

   Откроется файл проекта.

1. Удалите ссылки на `Microsoft.TypeScript.Default.props` и `Microsoft.TypeScript.targets`.

   Удаляемые импорты имеют примерно следующий вид:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```
