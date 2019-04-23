---
title: Создание кода в процессе построения
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 07f7c91c74961fa846abb70637f358de59d0eb94
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117100"
---
# <a name="code-generation-in-a-build-process"></a>Создание кода в процессе построения

[Преобразование текста](../modeling/code-generation-and-t4-text-templates.md) может вызываться как часть [процесс сборки](/azure/devops/pipelines/index) решения Visual Studio. Имеются задачи сборки, которые специализируются на преобразовании текста. Задачи сборки T4 запускают выполнение текстовых шаблонов времени разработки, а также компилируют текстовые шаблоны времени выполнения (предварительно обработанные).

Возможности задач построения несколько отличаются в зависимости от используемого обработчика сборки. При построении решения в Visual Studio текстового шаблона можно получить доступ к API Visual Studio (EnvDTE) Если [hostspecific = «true»](../modeling/t4-template-directive.md) атрибут имеет значение. Однако это не так, при сборке решения из командной строки или при запуске сборки сервера с помощью Visual Studio. В таких случаях сборка выполняется в MSBuild и используется другой узел T4.

Это означает, что вы не может получить доступ к таких вещей, как имена файлов проекта таким же образом при сборке текстового шаблона в MSBuild. Тем не менее, вы можете [передать данные среды в текстовые шаблоны и процессоры директив с помощью параметров сборки](#parameters).

## <a name="buildserver"></a> Настройка компьютеров

Чтобы включить задачи сборки на компьютере разработчика, установите пакет SDK моделирования для Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Если [сервер сборки](/azure/devops/pipelines/agents/agents) работает на компьютере, на котором не установлена Visual Studio, скопируйте следующие файлы на компьютер построения с компьютера разработки. Замените номером последней версии для "*".

- $(ProgramFiles)\MSBuild\Microsoft\VisualStudio\v*.0\TextTemplating

    - Microsoft.VisualStudio.TextTemplating.Sdk.Host.*.0.dll

    - Microsoft.TextTemplating.Build.Tasks.dll

    - Microsoft.TextTemplating.targets

- $(ProgramFiles)\Microsoft Visual Studio *.0\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

    - Microsoft.VisualStudio.TextTemplating.*.0.dll

    - Microsoft.VisualStudio.TextTemplating.Interfaces.*.0.dll (several files)

    - Microsoft.VisualStudio.TextTemplating.VSHost.*.0.dll

- $(ProgramFiles)\Microsoft Visual Studio *.0\Common7\IDE\PublicAssemblies\

    - Microsoft.VisualStudio.TextTemplating.Modeling.*.0.dll

## <a name="to-edit-the-project-file"></a>Изменение файла проекта

Вам придется изменить файл проекта для настройки некоторых функций в MSBuild.

В **обозревателе решений**, выберите **Unload** из контекстного меню проекта. Это позволит изменить CSPROJ- или VBPROJ-файл в редакторе XML.

После завершения редактирования, выберите **перезагрузить**.

## <a name="import-the-text-transformation-targets"></a>Импорт целевых объектов преобразования текста

В VBPROJ- или CSPROJ-файле найдите строку, аналогичную следующей:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- или -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

После этой строки вставьте директиву импорта текстового шаблона:

```xml
<!-- Optionally make the import portable across VS versions -->
  <PropertyGroup>
    <!-- Get the Visual Studio version: -->
    <VisualStudioVersion Condition="'$(VisualStudioVersion)' == ''">16.0</VisualStudioVersion>
    <!-- Keep the next element all on one line: -->
    <VSToolsPath Condition="'$(VSToolsPath)' == ''">$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)</VSToolsPath>
  </PropertyGroup>

<!-- This is the important line: -->
  <Import Project="$(VSToolsPath)\TextTemplating\Microsoft.TextTemplating.targets" />
```

## <a name="transform-templates-in-a-build"></a>Преобразование шаблонов в сборке

Предусмотрено несколько свойств, которые можно вставлять в файл проекта для управления задачей преобразования.

- Выполнять задачу преобразования в начале каждой сборки:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Перезаписывать файлы, доступные только для чтения (например, потому что они не извлечены):

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Каждый раз преобразовывать все шаблоны:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     По умолчанию задача MSBuild T4 заново генерирует выходной файл, если он старше своего файла шаблона, любого из включенных файлов или любого файла, который ранее считывался шаблоном или используемым им процессором директив. Обратите внимание, что это намного более мощная проверка зависимостей, чем используемая в команде "Преобразовать все шаблоны" в Visual Studio, которая только сравнивает даты шаблона и выходного файла.

Чтобы выполнить только преобразования текста в проекте, вызовите задачу TransformAll:

`msbuild myProject.csproj /t:TransformAll`

Чтобы преобразовать определенный текстовый шаблон:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

В команде TransformFile можно использовать символы подстановки:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Система управления версиями

Не существует специальной встроенной интеграции с системой управления версиями. Однако можно добавить собственные расширения, например, для извлечения и возврата созданного файла. По умолчанию задача преобразования текста избегает перезаписи файла, помеченного как доступный только для чтения, и если такой файл встречается, в список ошибок Visual Studio записывается информация об ошибке и выполнение задачи завершается неудачей.

Чтобы указать, что доступные только для чтения файлы следует перезаписывать, вставьте такое свойство:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Если не настроить шаг постобработки, при перезаписи файла в список ошибок будет записываться информация об ошибке.

## <a name="customize-the-build-process"></a>Настройки процесса построения

Преобразование текста производится перед выполнением других задач в процессе сборки. Задачи, которые вызываются до и после преобразования, можно задавать, устанавливая свойства `$(BeforeTransform)` и `$(AfterTransform)`.

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
  </PropertyGroup>
  <Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
  </Target>
  <Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
  </Target>
```

В свойстве `AfterTransform` можно указывать списки файлов:

- GeneratedFiles – список файлов, сгенерированных данным процессом. Для тех файлов, которые перезаписывают имеющиеся доступные только для чтения файлы, свойство %(GeneratedFiles.ReadOnlyFileOverwritten) будет иметь значение true. Эти файлы можно извлекать из системы управления версиями.

- NonGeneratedFiles – список доступных только для чтения файлов, которые не были перезаписаны.

Например, можно определить задачу для извлечения GeneratedFiles.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath и OutputFileName

Эти свойства используются только в MSBuild. Они не влияют на создание кода в Visual Studio. Они перенаправляют созданный выходной файл в другую папку или файл. Целевая папка должна уже существовать.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Для перенаправления может быть полезна папка `$(IntermediateOutputPath).`

Если указано имя выходного файла, оно получает приоритет над расширением, определенным в директиве output в шаблонах.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Свойства OutputFileName или OutputFilePath не рекомендуется указывать также при преобразовании шаблонов в VS с помощью преобразования всех или запуске генератора единственного файла. В результате путь к файлу будет зависеть от способа запуска преобразования. Это может быть очень неудобно.

## <a name="add-reference-and-include-paths"></a>Добавить ссылку и пути включения

Узел имеет набор путей по умолчанию, по которым производится поиск сборок, указанных в шаблонах. Для добавления в этот набор:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Чтобы задать папки, в которых будет производиться поиск включаемых файлов, укажите список через точку с запятой. Обычно производится добавление в существующий список папок.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="parameters"></a> Передача данных контекста сборки в шаблоны

Можно задать значения параметров в файле проекта. Например, можно передать [построения](../msbuild/msbuild-properties.md) свойства и [переменные среды](../msbuild/how-to-use-environment-variables-in-a-build.md):

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

В текстовом шаблоне задайте атрибут `hostspecific` в директиве template. Используйте [параметр](../modeling/t4-parameter-directive.md) директиву, чтобы получить значения:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

В процессоре директив можно вызвать [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)):

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue` получает данные из `T4ParameterValues` только при использовании MSBuild. При преобразовании шаблона с помощью Visual Studio параметры будут иметь значения по умолчанию.

## <a name="msbuild"></a> Использование свойств проекта в сборки и директивы #include

Макросы Visual Studio, такие как **$(SolutionDir)** не работают в MSBuild. Вместо этого можно использовать свойства проекта.

Изменить ваш *.csproj* или *.vbproj* файл для определения свойства проекта. В этом примере определяется свойство с именем **myLibFolder**:

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Теперь можно использовать ваше свойство проекта в директивах assembly и include:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

Эти директивы получают значения из T4parameterValues как в узлах MSBuild, так и в узлах Visual Studio.

## <a name="q--a"></a>Вопросы и ответы

**Зачем преобразование шаблонов на сервере сборки? Я уже преобразовал шаблоны в Visual Studio до возврата в моем коде.**

При обновлении включенного файла, или другой файл, считываемого шаблоном, Visual Studio не преобразует файл автоматически. Преобразование шаблонов в процессе сборки гарантирует, что все находится в актуальном состоянии.

**Какие другие варианты есть для преобразования текстовых шаблонов?**

- [Служебной программы TextTransform](../modeling/generating-files-with-the-texttransform-utility.md) можно использовать в командных сценариев. В большинстве случаев проще в использовании MSBuild.

- [Вызов преобразования текста в расширении VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)

- [Во время разработки текстовые шаблоны](../modeling/design-time-code-generation-by-using-t4-text-templates.md) преобразуются в Visual Studio.

- [Текстовые шаблоны времени выполнения](../modeling/run-time-text-generation-with-t4-text-templates.md) преобразуется во время выполнения в приложении.

## <a name="see-also"></a>См. также

::: moniker range="vs-2017"

- Есть хорошее руководство в шаблоне T4 MSbuild в *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets*

::: moniker-end

::: moniker range=">=vs-2019"

- Есть хорошее руководство в шаблоне T4 MSbuild в *% ProgramFiles (x86) %\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets*

::: moniker-end

- [Запись текстового шаблона T4](../modeling/writing-a-t4-text-template.md)
