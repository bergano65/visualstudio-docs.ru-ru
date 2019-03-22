---
title: Расширяемость проектов Visual C++
ms.date: 01/25/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a524d242f5c3fb146f3446cd0c020b01e130277c
ms.sourcegitcommit: 5af29226aef0a3b4a506b69a08a97cfd21049521
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58268729"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio проект C++ расширяемости и набора средств интеграции системы

Система проектов Visual C++ используется для файлов с расширением VCXPROJ. Он основан на [Visual Studio распространенных система проектов (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) и предоставляет дополнительные идентификаторы, расширяемость для конкретного C++ указывает для облегчения интеграции новые наборы инструментов, архитектур сборки и целевых платформ.

## <a name="c-msbuild-targets-structure"></a>Структура целевые объекты MSBuild для C++

Все файлы с расширением VCXPROJ импортировать эти файлы:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Эти файлы определяют мало сами по себе. Вместо этого они Импорт других файлов, на основе значений этих свойств:

- `$(ApplicationType)`

   Примеры Windows Store, Android, Linux

- `$(ApplicationTypeRevision)`

   Это должен быть строкой допустимой версии из формы основной_номер_версии.дополнительный_номер_версии[.построение[.редакция]].

   Примеры 1.0, 10.0.0.0

- `$(Platform)`

   В архитектуре сборки с именем «Платформа» по историческим причинам.

   Примеры Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Примеры: v140, v141, v141_xp, llvm

Эти значения свойства определяют имена папок в разделе `$(VCTargetsPath)` корневую папку:

`$(VCTargetsPath)`\\ &nbsp;&nbsp;&nbsp;&nbsp;*Тип приложения* \\ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(ApplicationType)` \\ &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ &nbsp;&nbsp;&nbsp;&nbsp;  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *Платформ* \\ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)` \\ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *PlatformToolsets* \\ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` &nbsp;&nbsp;&nbsp;&nbsp;настроекплатформ\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Используется, когда `$(ApplicationType)` пусто, для проектов Windows Desktop) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

### <a name="add-a-new-platform-toolset"></a>Добавить новый набор инструментов платформы

Чтобы добавить новый набор инструментов, например, «MyToolset» для существующей платформы Win32, создайте *MyToolset* папке `$(VCTargetsPath)`  *\\платформ\\Win32\\ PlatformToolsets\\*и создайте *Toolset.props* и *Toolset.targets* в нем файлов.

Каждое имя папки в разделе *PlatformToolsets* отображается в **свойства проекта** диалоговое окно как свободный **набор инструментов платформы** для определенной платформы, как показано ниже:

![Свойство набора инструментов платформы, в диалоговом окне страницы свойств проекта](media/vc-project-extensibility-platform-toolset-property.png "свойство набора инструментов платформы, в диалоговом окне страницы свойств проекта")

Создайте аналогичный *MyToolset* папок и *Toolset.props* и *Toolset.targets* файлов в каждой существующей папке платформа поддерживает этого набора инструментов.

### <a name="add-a-new-platform"></a>Добавить новую платформу

Чтобы добавить новую платформу, например, «MyPlatform», создайте *MyPlatform* папке `$(VCTargetsPath)`  *\\платформ\\*и создайте  *Platform.Default.props*, *Platform.props*, и *Platform.targets* в нем файлов. Также создайте `$(VCTargetsPath)`  *\\платформ\\*<strong><em>MyPlatform</em></strong>*\\PlatformToolsets\\*  папки и создать по крайней мере один набор инструментов в нем.

Все имена папок в разделе *платформ* папку для каждого `$(ApplicationType)` и `$(ApplicationTypeRevision)` отображаются в интегрированной среде разработки, как доступная **платформы** варианты для проекта.

![Новый Выбор платформы в диалоговом окне Создание платформы проекта](media/vc-project-extensibility-new-project-platform.png "New выбранной платформы в диалоговом окне Создание платформы проекта")

### <a name="add-a-new-application-type"></a>Добавить новый тип приложения

Чтобы добавить новый тип приложения, создайте *MyApplicationType* папке `$(VCTargetsPath)` *\\тип приложения\\* и создайте *Defaults.props* файл в ней. По крайней мере одной версии является обязательным для типа приложения, поэтому также создать `$(VCTargetsPath)`  *\\тип приложения\\MyApplicationType\\1.0* папки и создайте  *Defaults.props* файл в ней. Необходимо также создать `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\платформ* папки и создайте хотя бы одну платформу, в нем.

`$(ApplicationType)` и `$(ApplicationTypeRevision)` свойства не отображаются в пользовательском интерфейсе. Они определяются в шаблонах проектов и нельзя изменить после создания проекта.

## <a name="the-vcxproj-import-tree"></a>Дерево импорта VCXPROJ-файл

Упрощенное дерево операций импорта для файлов свойств и целевых объектов в Microsoft C++ выглядит так:

`$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(MSBuildExtensionsPath)` \\ `$(MSBuildToolsVersion)` \\ *Microsoft.Common.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportBefore*\\*по умолчанию* \\ \*. *props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *тип приложения* \\ `$(ApplicationType)` \\ *Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *тип приложения* \\ `$(ApplicationType)` \\ `$(ApplicationTypeRevision)` \\ *Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Тип приложения*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*платформ* \\ `$(Platform)` \\ *Platform.default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportAfter*\\*по умолчанию*\\\*. *PROPS*

Не задавать значение проектов рабочего стола Windows `$(ApplicationType)`, поэтому они импортировать только

`$(VCTargetsPath)`\\*Microsoft.Cpp.Default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(MSBuildExtensionsPath)` \\ `$(MSBuildToolsVersion)` \\ *Microsoft.Common.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportBefore*\\*по умолчанию* \\ \*. *props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *платформ* \\ `$(Platform)` \\ *Platform.default.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *ImportAfter* \\  *По умолчанию*\\\*. *PROPS*

Мы будем использовать `$(_PlatformFolder)` свойство для хранения `$(Platform)` папки платформы. Это свойство является

`$(VCTargetsPath)`\\*Платформы*\\`$(Platform)`

для классических приложений Windows и

`$(VCTargetsPath)`\\*Тип приложения*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*платформ*\\`$(Platform)`

для всего остального.

Файлы свойств импортируются в следующем порядке:

`$(VCTargetsPath)`\\*Microsoft.Cpp.props* &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *Platform.props* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Microsoft.Cpp.Platform.props* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *ImportBefore* \\\*. *PROPS* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props* &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ *</c152настроекImportAfter<spanclass="notranslate">*\\\*. *PROPS</span>*

Файлы целевых объектов импортируются в следующем порядке:

`$(VCTargetsPath)`\\*Microsoft.Cpp.targets* &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Microsoft.Cpp.Current.targets* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *Platform.targets* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(VCTargetsPath)` \\ *Microsoft.Cpp.Platform.targets*  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</c102настроек<spanclass="notranslate">&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *целевые объекты* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *PlatformToolsets* \\ `$(PlatformToolset)` \\ *Toolset.target* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; `$(_PlatformFolder)` \\ *ImportAfter* \\\*. *целевые объекты</span>*

Если вам нужно определить некоторые свойства по умолчанию для вашего набора инструментов, можно добавить файлы в соответствующие папки и ImportAfter.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Автор Toolset.props и Toolset.targets файлов

*Toolset.props* и *Toolset.targets* файлы имеют полный контроль над происходящим во время сборки, при использовании этого набора инструментов. Они также могут управлять доступных отладчиков, некоторые из пользовательского интерфейса интегрированной среды разработки, например содержимое **страницы свойств** диалоговое окно и некоторые другие аспекты поведения проекта.

Несмотря на то, что набор инструментов можно переопределить всего процесса сборки, обычно необходимо просто ваш набор инструментов для изменения или добавления, что некоторые этапы построения или использовать средства сборки, как часть существующего процесса сборки. Для достижения этой цели, существует ряд общих файлов свойств и целевых объектов, которые можно импортировать свой набор средств. В зависимости от нужных свой набор средств для выполнения эти файлы можно использовать для использования в качестве импортов, или в качестве примеров:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Этот файл определяет основные части этого процесса сборки в машинном, а также импортирует:

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Задает значения по умолчанию для наборов инструментов, используйте компиляторы Microsoft и предназначенных для Windows.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Этот файл определяет расположение пакета SDK для Windows, а также определяет некоторые важные свойства, для приложения, предназначенные для Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Интеграция целей набор инструментов имеет значения по умолчанию, процесс сборки C++

По умолчанию, процесс сборки C++ определяется в *Microsoft.CppCommon.targets*. Существует целевые объекты не вызывайте любые средства для определенной сборки; они определяют действия, их зависимости и порядок сборки основной.

Сборки C++ при наличии трех основных этапов, описанных в следующих целевых объектов:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Так как каждый шаг сборки может выполняться независимо друг от друга, целевых объектов, в один шаг нельзя полагаться на группы элементов и свойства, определенные в целевых объектах, которые работают как часть другом шаге. Это разделение позволяет определенные сборки оптимизации производительности. Несмотря на то, что он не используется по умолчанию, вы по-прежнему рекомендуется принять такое разделение.

Целевые объекты, которые выполняются в каждом шаге управляются эти свойства:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

У каждого действия также есть до и после свойства.

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

См. в разделе *Microsoft.CppBuild.targets* файл примеры целевых объектов, включенных в каждый шаг:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Если взглянуть на целевые объекты, такие как `_ClCompile`, вы увидите, они ничего не делать непосредственно сами по себе, но вместо этого зависят от других целевых объектов, включая `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` и другие сборки, целевые объекты конкретного инструмента определяются как пустые целевые объекты в *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Так как `ClCompile` целевого пуст, если только он переопределяется атрибутом набор инструментов, не выполняет никаких действий реальные сборки. Можно переопределить целевые объекты набора инструментов `ClCompile` целевой, то есть они могут содержать другую `ClCompile` определения после импорта *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Несмотря на свое название, который был создан до Visual Studio реализована поддержка разных платформ, `ClCompile` целевой объект не потребуется вызывать CL.exe. Он также может вызвать другие компиляторы, Clang и gcc с помощью соответствующих задач MSBuild.

`ClCompile` Целевому серверу должно быть не все зависимости, за исключением `SelectClCompile` целевой объект, который необходим для команды компиляции отдельного файла для работы в интегрированной среде разработки.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Задачи MSBuild для использования в целевых объектов набора инструментов

Чтобы вызвать средство собственно сборку, целевой объект должен вызвать задачу MSBuild. Что представляет собой простую [задача Exec](../msbuild/exec-task.md) , позволяющий указать командную строку для запуска. Тем не менее средства сборки, обычно имеют множество параметров, входных данных. и выходные данные для отслеживания добавочных сборок, поэтому более разумно иметь специальные задачи для них. Например `CL` задач преобразует свойства MSBuild в CL.exe коммутаторов, записывает их в файл ответов и вызывает CL.exe. Он также отслеживает все входные и выходные файлы для более поздней версии инкрементные сборки. Дополнительные сведения см. в разделе [инкрементные сборки и проверки наличия обновлений](#incremental-builds-and-up-to-date-checks).

Microsoft.Cpp.Common.Tasks.dll реализует эти задачи:

- `BSCMake`

- `CL`

- `ClangCompile` (clang gcc коммутаторами)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (такие как Exec, но с вводом и выводом отслеживания)

- `SetEnv`

- `GetOutOfDateItems`

Если у вас есть средство, работает так же, как существующие средства и с аналогичные параметры командной строки (подобно clang-cl или CL), ту же задачу можно использовать для них.

Если вам нужно создать новую задачу для средства построения, можно выбрать из следующих вариантов:

1. Если эта задача используется редко, или через несколько секунд не имеет значения для построения, можно использовать задачи MSBuild «inline»:

   - Задача XAML (настраиваемое правило построения)

     Один пример объявления задачи Xaml, см. в разделе `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*и его использования см. в разделе `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Задача кода](../msbuild/msbuild-inline-tasks.md)

1. Если требуется повысить производительность задачи или достаточно более сложные функции, используйте регулярное MSBuild [написание задач](../msbuild/task-writing.md) процесса.

   Если не все входные и выходные данные средства перечислены в командной строке средства, как в `CL`, `MIDL`, и `RC` случаи и при необходимости автоматическое входных и выходных данных файла отслеживания, а также создания файла .tlog производными ваша задача `Microsoft.Build.CPPTasks.TrackedVCToolTask`класса. В настоящее время, пока есть документация по базе [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) класса, примеры и документацию, сведения о отсутствуют `TrackedVCToolTask` класса. Если это особый интерес, добавить свой голос к запросу на [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Инкрементные сборки и проверки наличия обновлений

Инкрементное построение MSBuild по умолчанию предназначен для использования `Inputs` и `Outputs` атрибуты. Если вы укажете их, MSBuild вызывает целевой объект только в том случае, если входные данные имеют имеет более новую временную метку, чем все выходные данные. Так как исходные файлы часто включают или импортировать другие файлы и создавать средства создают различные выходы в зависимости от параметров инструмента, его трудно указать всех возможных входных значений и выходных данных целевых объектов MSBuild.

Для управления этой проблемы, сборки C++ используется другой метод для поддержки инкрементных сборок. Большинство целевых объектов не указать входные и выходные данные и таким образом, всегда выполняются во время сборки. Задачи, которые вызваны целевых объектов записи сведения обо всех входных данных и выдает в *tlog* файлы с расширением .tlog. TLOG-файлы используются более поздних выпусков для проверки, что был изменен и необходимо перестроить, и что актуален. TLOG-файлы также являются единственным источником для проверки наличия обновлений сборки по умолчанию в интегрированной среде разработки.

Чтобы определить, все входные и выходные данные, задачи инструментов машинного кода используйте tracker.exe и [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) класса, предоставляемым MSBuild.

Определяет Microsoft.Build.CPPTasks.Common.dll `TrackedVCToolTask` открытого абстрактного базового класса. Большинство задач, инструментов машинного кода являются производными от этого класса.

Начиная с Visual Studio 2017 с обновлением 15.8, можно использовать `GetOutOfDateItems` реализации в Microsoft.Cpp.Common.Tasks.dll для создания TLOG-файлы для пользовательских целевых объектов с помощью известных входных и выходных данных задачи.
Кроме того, их можно создать с помощью `WriteLinesToFile` задачи. См. в разделе `_WriteMasmTlogs` target в `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* в качестве примера.

## <a name="tlog-files"></a>интерпретируемые TLOG-файлы

Существует три типа TLOG-файлы: *чтение*, *записи*, и *командной строки*. TLOG-файлы, предназначенные для чтения и записи используются инкрементные сборки и проверки наличия обновлений в интегрированной среде разработки. Командной строки TLOG-файлы используются только в инкрементные сборки.

MSBuild предоставляет эти вспомогательные классы для чтения и записи TLOG-файлы:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) класс может использоваться для доступа чтения и записи TLOG-файлы, а также для идентификации входных данных, которые являются более новыми, чем выходные данные или если отсутствуют выходные данные. Он используется в проверку обновлений.

Командной строки TLOG-файлы содержат сведения о командных строк, используемых в построении. Они используются только для инкрементных сборок без последних обновлений проверки, поэтому внутренний формат определяется задачу MSBuild, которая создает их.


### <a name="read-tlog-format"></a>Формат .tlog чтения

*Чтение* TLOG-файлы (\*.read.\*. TLOG) содержит сведения об исходных файлов и их зависимости.

Символ каретки (**^**) в начале строки указывает один или несколько источников. Источники, которые совместно используют такие же зависимости разделяются символом вертикальной черты (**\|**).

Файлы зависимостей, перечислены после источников, каждый на отдельной строке. Все имена файлов являются полные пути.

Предположим, например, источники проекта находятся в *F:\\тестирования\\ConsoleApplication1\\ConsoleApplication1*. Если исходный файл, *Class1.cpp*, имеет следующие включает,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

затем *CL.read.1.tlog* файл содержит исходного файла, а затем его две зависимости:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Он не требуется писать имена файлов в верхний регистр, но это удобный способ для некоторых средств.

### <a name="write-tlog-format"></a>Запись .tlog формат

*Запись* .tlog (\*.write.\*. файлы журнала отслеживания) соединения с источниками и выходные данные.

Символ каретки (**^**) в начале строки указывает один или несколько источников. Несколько источников разделяются символом вертикальной черты (**\|**).

Выходные файлы, созданные из источников, должно быть указано после источников, каждый на отдельной строке. Все имена файлов должны быть полные пути.

Например, для простого проекта ConsoleApplication с файлом дополнительных исходных *Class1.cpp*, *link.write.1.tlog* файл может содержать:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Сборки времени разработки

В интегрированной среде разработки, .vcxproj проекты используют набор целевых объектов MSBuild для получения дополнительных сведений из проекта и повторно создать выходные файлы. Некоторые из этих целевых объектов используются только в сборки во время разработки, но многие из них используются в обычной сборки и сборки во время разработки.

Общие сведения о сборки во время разработки, см. в документации CPS для [сборки времени разработки](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Эта документация применяется только частично для проектов Visual C++.

`CompileDesignTime` И `Compile` целевых объектов, упомянутые во время разработки сборки никогда не запускавшиеся для проектов VCXPROJ-файл документации. С расширением VCXPROJ проекты Visual C++ позволяет получить сведения IntelliSense различных целей разработки.

### <a name="design-time-targets-for-intellisense-information"></a>Целевые объекты во время разработки сведения IntelliSense

В определенных целевых объектов во время разработки, используемым в проектах с расширением VCXPROJ `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

`GetClCommandLines` Цель собирает параметры компилятора для IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` — во время разработки только целевые объекты, необходимые для разработки сборки инициализации. Помимо прочего эти целевые объекты отключить некоторые функции обычного построения для повышения производительности.

- `ComputeCompileInputsTargets` — набор целевых объектов, который изменяет параметры компилятора и элементов. Эти целевые объекты выполняются в во время разработки и регулярных сборок.

Вызовы целевой `CLCommandLine` задачи для создания командной строки, используемых средством IntelliSense. Опять же несмотря на свое название, он может обрабатывать не только параметров CL, но также доступны возможности Clang и gcc. Тип параметров компилятора управляется `ClangMode` свойство.

В настоящее время командной строки, созданные `CLCommandLine` задачи всегда использует коммутаторы CL (даже в режиме Clang), так как их легко модуля IntelliSense невозможна для синтаксического анализа.

Если вы добавляете целевой объект, который выполняется перед компиляцией, регулярные или разработки, убедитесь, что он не нарушает работу во время разработки построения или повлиять на производительность. — Это самый простой способ тестирования на целевом сервере откройте командную строку разработчика и выполните следующую команду:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

Эта команда создает подробный журнал, *msbuild.log*, приводит к производительности, сводка задач и целевых объектов в конце.

Обязательно используйте `Condition ="'$(DesignTimeBuild)' != 'true'"` во всех операциях, которые имеют только смысл для обычной сборки, а не для сборки во время разработки.

### <a name="design-time-targets-that-generate-sources"></a>Целевые объекты во время разработки, создания источников

*Эта функция отключена по умолчанию для проектов классических приложений собственного и сейчас не поддерживается в проектах кэшированных*.

Если `GeneratorTarget` метаданных определено для элемента проекта, целевой объект выполняется автоматически и при загрузке проекта, и при изменении исходного файла.

::: moniker range="vs-2017"

Например, для автоматического создания CPP или h файлов из XAML-файлы, `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* файлы определения этих сущности:

::: moniker-end

::: moniker range=">=vs-2019"

Например, для автоматического создания CPP или h файлов из XAML-файлы, `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*v16.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* файлы определения этих сущности:

::: moniker-end

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Чтобы использовать `Task.HostObject` для получения несохраненные содержимого исходных файлов, задач и целевых объектов должен быть зарегистрирован как [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) для заданного проектов в pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Расширяемость проектов Visual C++ в Интегрированной среде разработки Visual Studio

Система проектов Visual C++ основана на [система проектов VS](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)и использует точки расширения. Тем не менее реализации иерархии проекта в Visual C++ и не основан на CPS, поэтому расширяемость иерархии ограничен элементов проекта.

### <a name="project-property-pages"></a>Страницы свойств проекта

Общие сведения, см. в разделе [Framework многоплатформенного нацеливания для проектов VC ++](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

Проще говоря, на страницах свойств вы увидите в **свойства проекта** диалоговое окно для проекта C++ определяются *правило* файлов. Файл правил задает набор свойств для отображения на странице свойств и как и их сохранения в проекте файл. Файлы правил — это файлы XML, использующих формат Xaml. Описываются типы, используемые для сериализации их в [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Дополнительные сведения об использовании файлов правил в проектах см. в разделе [файлы правил XML страницы свойство](/cpp/build/reference/property-page-xml-files).

Необходимо добавить файлы правил `PropertyPageSchema` группы элементов:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` ограничения правил метаданных, который управляется также тип правила и может иметь одно из следующих значений:

`Project` | `File` | `PropertySheet`

CPS поддерживает другие значения для типа контекста, но они не используются в проектах Visual C++.

Если правило должен быть видимым в нескольких контекстах, используйте точку с запятой (**;**) для разделения значения контекста, как показано ниже:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Формат правила, а также основные типы

Формат правила проста, поэтому в этом разделе описывается только атрибуты, влияющие на внешний вид правило в пользовательском интерфейсе.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate` Атрибут определяет, как правило, отображается в **страницы свойств** диалоговое окно. Атрибут может иметь одно из следующих значений:

| Атрибут | Описание: |
|------------| - |
| `generic` | Все свойства отображаются на одной странице под заголовками по категориям<br/>Правила могут быть отображены для `Project` и `PropertySheet` контекстов, но не `File`.<br/><br/> Пример `$(VCTargetsPath)`\\*1033*\\*general.xml* |
| `tool` | Категории отображаются в виде вложенных.<br/>Правила могут быть отображены во всех контекстах: `Project`, `PropertySheet` и `File`.<br/>Правило является видимым в свойствах проекта, только в том случае, если проект не содержит элемента с `ItemType` определенные в `Rule.DataSource`, если имя правила не включена в `ProjectTools` группу элементов.<br/><br/>Пример `$(VCTargetsPath)`\\*1033*\\*clang.xml* |
| `debugger` | Страница будет отображена в составе отладка страницы.<br/>Категории в настоящее время учитываются.<br/>Имя правила должно совпадать с MEF средства запуска отладки объекта `ExportDebugger` атрибута.<br/><br/>Пример `$(VCTargetsPath)`\\*1033*\\*отладчик\_локального\_windows.xml* |
| *custom* | Пользовательский шаблон. Имя шаблона должно соответствовать `ExportPropertyPageUIFactoryProvider` атрибут `PropertyPageUIFactoryProvider` объект MEF. См. в разделе **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Пример `$(VCTargetsPath)`\\*1033*\\*userMacros.xml* |

Если в правиле используется один из шаблонов на основе сетки свойств, он может использовать эти точки расширения для его свойства:

- [Редакторы значений свойств](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Поставщик значений динамического перечисления](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Расширить правила

Если вы хотите использовать существующее правило, но нужно добавить или удалить (которые скрыть) лишь несколько свойств, можно создать [правило расширения](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Переопределить правило

Возможно, вам необходимо ваш набор инструментов, чтобы использовать большинство правил по умолчанию проекта, но заменить один или несколько из них. Например предположим, что вы хотите изменить правило, C/C++ для отображения параметров компилятора. Можно указать новое правило с таким именем и отображаемое имя, что и у существующего правила и включить ее в `PropertyPageSchema` группы позиций после импорта целевых объектов по умолчанию cpp. В проекте используется только одно правило с заданным именем, и последний включенных в `PropertyPageSchema` элемент группы wins.

#### <a name="project-items"></a>Элементы проекта

*ProjectItemsSchema.xml* файл определяет `ContentType` и `ItemType` значений для элементов, которые обрабатываются как элементы проекта, а также определяет `FileExtension` элементов, чтобы определить, какие группы элементов, добавляется новый файл.

Файл ProjectItemsSchema по умолчанию находится в `$(VCTargetsPath)` \\ *1033*\\*ProjectItemsSchema.xml*. Чтобы расширить его, необходимо создать файл схемы с новым именем, например *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Затем в файле целей, добавьте следующую команду:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Пример `$(VCTargetsPath)`\\*BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Отладчики

Службы отладки в Visual Studio поддерживает возможность расширения для обработчика отладки. Дополнительные сведения см. в этих примерах:

- [MIEngine, проект с открытым кодом, который поддерживает отладку lldb](https://github.com/Microsoft/MIEngine)

- [Пример ядра отладки Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Чтобы указать механизмы отладки и другие свойства для сеанса отладки, необходимо реализовать [средства запуска отладки](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) компонент MEF и добавьте `debugger` правило. Например, см. в разделе `$(VCTargetsPath)` \\1033\\отладчик\_локального\_windows.xml файл.

### <a name="deploy"></a>Развернуть

проекты с расширением VCXPROJ использование расширяемости система проектов Visual Studio для [развертывание поставщики](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Проверка наличия обновлений сборки

По умолчанию проверка наличия обновлений сборки требует чтения .tlog и записи TLOG-файлы в `$(TlogLocation)` папку во время сборки все сборки входных и выходных данных.

Чтобы использовать пользовательские проверка наличия обновлений:

1. Отключить проверку обновлений по умолчанию, добавив `NoVCDefaultBuildUpToDateCheckProvider` возможность *Toolset.targets* файла:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Реализовать свою собственную [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Обновление проекта

### <a name="default-vcxproj-project-upgrader"></a>Средство обновления проекта VCXPROJ-файл по умолчанию

Изменения программного обеспечения по умолчанию VCXPROJ-файл проекта `PlatformToolset`, `ApplicationTypeRevision`, набор инструментов MSBuild версии и .net framework. Последние два всегда изменяются значения по умолчанию версии Visual Studio, но `PlatformToolset` и `ApplicationTypeRevision` может управляться особые свойства MSBuild.

Средство обновления использует эти критерии, чтобы определить, можно ли обновить проект, или нет:

1. Для проектов, которые определяют `ApplicationType` и `ApplicationTypeRevision`, есть папка с более высоким номером редакции, отличный от текущего.

1. Свойство `_UpgradePlatformToolsetFor_<safe_toolset_name>` определенные для текущего набора инструментов, и его значение не равно текущий набор инструментов.

   В именах свойств  *\<safe_toolset_name >* представляет имя набора инструментов с использованием не буквенно-цифровых символов заменяется символом подчеркивания (**\_**).

При обновлении проекта он участвует *целевой платформы решения*. Дополнительные сведения см. в разделе [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Если вы хотите Декорирование имен проектов в **обозревателе решений** для проектов использования конкретных инструментов, `_PlatformToolsetShortNameFor_<safe_toolset_name>` свойство.

Примеры `_UpgradePlatformToolsetFor_<safe_toolset_name>` и `_PlatformToolsetShortNameFor_<safe_toolset_name>` определения свойств, см. в разделе *Microsoft.Cpp.Default.props* файла. Примеры использования см. в разделе `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* файла.

### <a name="custom-project-upgrader"></a>Средство обновления пользовательского проекта

Для использования объекта средство обновления пользовательского проекта, реализуйте компонент MEF, как показано ниже:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Код можно импортировать и вызов объекта средство обновления VCXPROJ-файл по умолчанию:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` определяется в *Microsoft.VisualStudio.ProjectSystem.VS.dll* и аналогичен `IVsRetargetProjectAsync`.

Определение `VCProjectUpgraderObjectName` свойство, чтобы сообщить системе проектов для использования объекта пользовательским средством обновления:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Отключить обновления проекта

Чтобы отключить обновления проектов, используйте `NoUpgrade` значение:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Кэш проекта и расширяемость

Для повышения производительности при работе с крупными решениями C++ в Visual Studio 2017, [проекта кэша](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) был введен. Она реализуется как база данных SQLite заполняются данными проекта, а затем использовать для загрузки проектов без загрузки проектов MSBuild или CPS в памяти.

Так как нет объектов CPS для проектов с расширением VCXPROJ, загруженных из кэша, расширения компонентов MEF, Импорт `UnconfiguredProject` или `ConfiguredProject` не может быть создан. Для поддержки расширяемости, проект кэш не используется, когда Visual Studio обнаруживает ли проект использует (или большей вероятностью будет использовать) расширений MEF.

Эти типы проектов, всегда должны быть полностью загружены и имеют CPS объектов в памяти, поэтому для них создаются все расширения MEF:

- Запускаемых проектов

- Проектов, содержащих средство обновления пользовательского проекта, то есть, они определяют `VCProjectUpgraderObjectName` свойство

- Проекты, не предназначенных для Windows Desktop, то есть, они определяют `ApplicationType` свойство

- Элементы проектов (.vcxitems) и все проекты, ссылка на общий их путем импорта .vcxitems проектов.

Если ни одно из этих условий не обнаружены, создается кэш проекта. Кэш содержит все данные из проекта MSBuild, необходимые для ответа `get` запрашивает на `VCProjectEngine` интерфейсов. Это означает, что все изменения в свойства MSBuild, и целевых объектов файловом уровне, выполненную расширением только в проекты, загруженные из кэша.

## <a name="shipping-your-extension"></a>Модуль доставки

Сведения о том, как создать VSIX-файлы, см. в разделе [доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Сведения о том, как добавить файлы установки специальные расположения, например, чтобы добавить файлы в `$(VCTargetsPath)`, см. в разделе [Установка за пределами папки расширений](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Дополнительные ресурсы

Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) предоставляет обработчик построения и расширяемый формат на основе XML для файлов проекта. Вы должны быть знакомы с basic [основные возможности MSBuild](../msbuild/msbuild-concepts.md) и с тем, как [MSBuild для Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) система проектов works для расширения Visual C++.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) предоставляет расширение API-интерфейсы, используемые CPS и система проектов Visual C++. Обзор использования MEF, CPS, см. в разделе [CPS и MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) в [VSProjectSystem Обзор MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Можно настроить существующие системы сборки для добавления этапов построения или новых типов файлов. Дополнительные сведения см. в разделе [Общие сведения о MSBuild (Visual C++)](/cpp/build/reference/msbuild-visual-cpp-overview) и [работа со свойствами проекта](/cpp/build/working-with-project-properties).
