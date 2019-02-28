---
title: Настройка сборки | Документы Майкрософт
ms.date: 06/14/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, transforms
- transforms [MSBuild]
ms.assetid: d0bceb3b-14fb-455c-805a-63acefa4b3ed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc4515ad8f61d749c9fb7552911bfb15dcc3471a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610337"
---
# <a name="customize-your-build-c-visual-basic"></a>Настройка сборки (C#, Visual Basic)

Проекты MSBuild, использующие стандартный процесс сборки (импорт *Microsoft.Common.props* и *Microsoft.Common.targets*), имеют несколько обработчиков расширяемости, позволяющих настроить процесс сборки.

## <a name="add-arguments-to-command-line-msbuild-invocations-for-your-project"></a>Добавление аргументов в вызовы командной строки MSBuild для проекта

Файл *Directory.Build.rsp*, расположенный в исходном каталоге или на более высоком уровне, применяется к сборкам из командной строки проекта. Дополнительные сведения см. в разделе [Файлы ответов MSBuild](../msbuild/msbuild-response-files.md#directorybuildrsp).

## <a name="directorybuildprops-and-directorybuildtargets"></a>Directory.Build.props и Directory.Build.targets

Чтобы указать новое настраиваемое свойство для проектов в решении, в версиях MSBuild до 15 приходилось вручную добавлять ссылку на это свойство в каждый файл проекта в решении. Либо приходилось определять свойство в файле *.props* и затем явно импортировать файл *.props* в каждый проект решения.

Но теперь вы можете добавить новое свойство в любой проект за один шаг, определив его в единственном файле *Directory.Build.props* в корневой папке с исходным кодом. При запуске MSBuild *Microsoft.Common.props* ищет файл *Directory.Build.props* в структуре каталогов (а *Microsoft.Common.targets* ищет файл *Directory.Build.targets*). Если он его находит, то импортирует свойство. Пользовательский файл *Directory.Build.props* содержит настройки персонализации для проектов в своем каталоге.

> [!NOTE]
> В файловых системах на основе Linux учитывается регистр. Убедитесь, что регистр имени файла Directory.Build.props полностью совпадает, иначе он не будет обнаружен во время сборки.
>
> Дополнительные сведения см. в [этой статье об ошибке на GitHub ](https://github.com/dotnet/core/issues/1991#issue-368441031).

### <a name="directorybuildprops-example"></a>Пример Directory.Build.props

Например, если вы хотите предоставить всем проектам новую функцию Roslyn **/deterministic** через свойство `$(Deterministic)` в целевом объекте Roslyn `CoreCompile`, можно сделать следующее.

1. Создайте в корне репозитория файл с именем *Directory.Build.props*.
2. Добавьте в этот файл приведенный ниже XML-код.

   ```xml
   <Project>
    <PropertyGroup>
      <Deterministic>true</Deterministic>
    </PropertyGroup>
   </Project>
   ```
3. Запустите MSBuild. Уже существующие в проекте файлы импорта *Microsoft.Common.props* и *Microsoft.Common.targets* находят новый файл и импортируют его.

### <a name="search-scope"></a>Область поиска

При поиске файла *Directory.Build.props* MSBuild обходит структуру каталогов вверх от расположения проекта (`$(MSBuildProjectFullPath)`). Когда файл найден, поиск останавливается. Например, если `$(MSBuildProjectFullPath)` имеет значение *c:\users\username\code\test\case1*, MSBuild начнет поиск там, а затем будет переходить вверх по структуре каталогов, пока не найдет файл *Directory.Build.props*. Пример такого поиска по структуре каталогов представлен ниже.

```
c:\users\username\code\test\case1
c:\users\username\code\test
c:\users\username\code
c:\users\username
c:\users
c:\
```

Расположение файла решения не имеет значения для *Directory.Build.props*.

### <a name="import-order"></a>Порядок импорта

*Directory.Build.props* импортируется в *Microsoft.Common.props* очень рано, поэтому определенные позднее свойства ему недоступны. Так что не ссылайтесь на свойства, которые еще не определены (и оцениваются как пустые).

*Directory.Build.targets* импортируется из *Microsoft.Common.targets* после импорта файлов *.targets* из пакетов NuGet. Таким образом, он переопределяет свойства и целевые объекты, определенные в большей части логики сборки, но иногда требуется настроить файл проекта после окончательного импорта.

### <a name="use-case-multi-level-merging"></a>Вариант использования: многоуровневое слияние

Предположим, что вы используете следующую стандартную структуру решения:

```
\
  MySolution.sln
  Directory.Build.props     (1)
  \src
    Directory.Build.props   (2-src)
    \Project1
    \Project2
  \test
    Directory.Build.props   (2-test)
    \Project1Tests
    \Project2Tests
```

Допустим, вам нужны некоторые общие свойства для всех проектов *(1)*, а также общие свойства для проектов *исходного кода* *(2-src)* и общие свойства для проектов *тестирования* *(2-test)*.

Чтобы система MSBuild правильно объединила "внутренние" файлы (*2-src* и *2-test*) с "внешним" файлом (*1*), обязательно учитывайте, что MSBuild прекращает сканирование при обнаружении файла *Directory.Build.props*. Чтобы продолжить сканирование и включить в слияние внешний файл, добавьте в оба внутренних файла следующее:

`<Import Project="$([MSBuild]::GetPathOfFileAbove('Directory.Build.props', '$(MSBuildThisFileDirectory)../'))" />`

Ниже кратко описан основной алгоритм работы MSBuild.

- Для каждого проекта MSBuild находит ближайший файл *Directory.Build.props*, расположенный выше в структуре решения, объединяет его с параметрами по умолчанию и на этом останавливает сканирование.
- Если вы хотите обнаружить и объединить несколько уровней, импортируйте "внешний" файл из "внутреннего", как показано выше ([`<Import...>`](../msbuild/property-functions.md#msbuild-getpathoffileabove)).
- Если "внешний" файл сам не импортирует ничего, расположенного выше, то сканирование останавливается здесь.
- Для управления процессом сканирования и слияния используйте `$(DirectoryBuildPropsPath)` и `$(ImportDirectoryBuildProps)`.

Проще говоря, MSBuild останавливает поиск на первом файле *Directory.Build.props*, который ничего не импортирует.

## <a name="msbuildprojectextensionspath"></a>MSBuildProjectExtensionsPath

По умолчанию *Microsoft.Common.props* импортирует `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.props`, а *Microsoft.Common.targets* импортирует `$(MSBuildProjectExtensionsPath)$(MSBuildProjectFile).*.targets`. По умолчанию `MSBuildProjectExtensionsPath` имеет значение `$(BaseIntermediateOutputPath)`, `obj/`. NuGet использует этот механизм для ссылки на логику сборки, предоставляемую вместе с пакетами. Например, во время восстановления он создает файлы `{project}.nuget.g.props`, ссылающиеся на содержимое пакета.

Этот механизм расширяемости можно отключить, установив для свойства `ImportProjectExtensionProps` значение `false` в *Directory.Build.props* или до импорта *Microsoft.Common.props*.

> [!NOTE]
> Отключение импортов MSBuildProjectExtensionsPath препятствует применению логики сборки, предоставляемой в пакетах NuGet, к проекту. Некоторым пакетам NuGet нужна работающая логика сборки, и если эта возможность отключена, они будут бесполезны.

## <a name="user-file"></a>Файл USER

*Microsoft.Common.CurrentVersion.targets* импортирует `$(MSBuildProjectFullPath).user`, если он существует, поэтому можно создать файл рядом с проектом с этим дополнительным расширением. Для долгосрочных изменений, которые вы собираетесь возвратить в систему управления версиями, рекомендуется изменить сам проект, чтобы тем, кто впоследствии будет обслуживать программу, не потребовалось разбираться в этом механизме расширения.

## <a name="msbuildextensionspath-and-msbuilduserextensionspath"></a>MSBuildExtensionsPath и MSBuildUserExtensionsPath

> [!WARNING]
> Использование этих механизмов расширения затрудняет получение повторяемых сборок на разных компьютерах. Попробуйте использовать конфигурацию, которую можно возвратить в систему управления версиями и предоставить для общего доступа всем разработчикам базы кода.

По соглашению многие файлы базовой логики сборки импортируют

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportBefore\*.targets
```

перед своим содержимым и

```xml
$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\{TargetFileName}\ImportAfter\*.targets
```

после него. Это позволяет установленным пакетам SDK дополнять логику сборки распространенных типов проектов.

Поиск по той же структуре каталогов выполняется в `$(MSBuildUserExtensionsPath)`, который является папкой конкретного пользователя *%LOCALAPPDATA%\Microsoft\MSBuild*. Файлы, помещенные в эту папку, импортируются для всех сборок соответствующего типа проекта, выполняемого с использованием учетных данных этого пользователя. Пользовательские расширения можно отключить, задав свойства, имя которых соответствует импортируемому файлу по шаблону `ImportUserLocationsByWildcardBefore{ImportingFileNameWithNoDots}`. Например, установив для `ImportUserLocationsByWildcardBeforeMicrosoftCommonProps` значение `false`, можно препятствовать импорту `$(MSBuildUserExtensionsPath)\$(MSBuildToolsVersion)\Imports\Microsoft.Common.props\ImportBefore\*`.

## <a name="customize-the-solution-build"></a>Настройка сборки решения

> [!IMPORTANT]
> Подобная настройка сборки решения применяется только к сборкам из командной строки с *MSBuild.exe*. Она **не** применяется к сборкам внутри Visual Studio.

Когда система MSBuild выполняет сборку файла решения, она сначала внутренне преобразует его в файл проекта и затем выполняет его сборку. Созданный файл проекта импортирует `before.{solutionname}.sln.targets` до определения каких-либо целевых объектов и `after.{solutionname}.sln.targets` после их импорта, включая целевые объекты, установленные в каталоги `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportBefore` и `$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\SolutionFile\ImportAfter`.

Например, можно определить новый целевой объект для записи настраиваемого сообщения журнала после сборки *MyCustomizedSolution.sln*, создав в том же каталоге файл *after.MyCustomizedSolution.sln.targets*, содержащий следующее:

```xml
<Project>
 <Target Name="EmitCustomMessage" AfterTargets="Build">
   <Message Importance="High" Text="The solution has completed the Build target" />
 </Target>
</Project>
```

## <a name="see-also"></a>См. также

- [Основные понятия MSBuild](../msbuild/msbuild-concepts.md)

- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
