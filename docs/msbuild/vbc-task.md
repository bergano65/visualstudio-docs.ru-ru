---
title: Задача Vbc| Документация Майкрософт
description: Узнайте об использовании задачи Vbc в MSBuild для создания программы-оболочки для файла vbc.exe, который создает исполняемые файлы, библиотеки динамической компоновки или модули кода.
ms.custom: SEO-VS-2020
ms.date: 04/12/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6596dd0893d0ab302a738cb12856fc6758df039
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908869"
---
# <a name="vbc-task"></a>Vbc - задача

Использует программу-оболочку для файла *vbc.exe*, который создает исполняемые файлы (*EXE-файлы*), библиотеки динамической компоновки (*DLL-файлы*) или модули кода ( *.netmodule*). Дополнительные сведения о файле *vbc.exe* см. в разделе [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `Vbc` .

| Параметр | Описание |
|------------------------------| - |
| `AdditionalLibPaths` | Необязательный параметр `String[]`.<br /><br /> Задает дополнительные папки, в которых выполняется поиск сборок, указанных в атрибуте References. |
| `AddModules` | Необязательный параметр `String[]`.<br /><br /> Дает компилятору указание сделать всю информацию о типах из указанных файлов доступной компилируемому проекту. Этот параметр соответствует параметру [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) компилятора *vbc.exe*. |
| `BaseAddress` | Необязательный параметр `String`.<br /><br /> Задает базовый адрес библиотеки DLL. Этот параметр соответствует параметру [-baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) компилятора *vbc.exe*. |
| `CodePage` | Необязательный параметр `Int32`.<br /><br /> Задает кодовую страницу, которая будет использоваться для всех файлов исходного кода при компиляции. Этот параметр соответствует параметру [-codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) компилятора *vbc.exe*. |
| `DebugType` | Необязательный параметр `String[]`.<br /><br /> Указывает компилятору создать отладочную информацию. Этот параметр может иметь следующие значения:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> По умолчанию задано значение `full`, разрешающее подключение отладчика к исполняемой программе. Значение `pdbonly` позволяет выполнять отладку исходного кода при запуске программы в отладчике, но при этом код языка сборки отображается только при подключении выполняющейся программы к отладчику. Дополнительные сведения см. в разделе [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Необязательный параметр `String[]`.<br /><br /> Задает константы условной компиляции. Пары "символ — значение" разделяются точками с запятой и задаются с использованием следующего синтаксиса.<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Этот параметр соответствует параметру [-define](/dotnet/visual-basic/reference/command-line-compiler/define) компилятора *vbc.exe*. |
| `DelaySign` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, задача помещает открытый ключ в сборку. Если присвоено значение `false`, задача полностью подписывает сборку. Значение по умолчанию — `false`. Этот параметр действует только при использовании параметра `KeyFile` или `KeyContainer`. Этот параметр соответствует параметру [-delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) компилятора *vbc.exe*. |
| `Deterministic` | Необязательный параметр `Boolean`.<br/><br/> Если задано значение `true`, компилятор будет выдавать сборку, чье двоичное содержимое идентично в разных компиляциях, если входные данные идентичны.<br/><br/>Дополнительные сведения см. в разделе [-deterministic](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Необязательный параметр `String`.<br /><br /> Подавляет указанные предупреждения. Необходимо указать только числовую часть идентификатора предупреждения. При указании нескольких предупреждений они отделяются друг от друга точкой с запятой. Этот параметр соответствует параметру [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) компилятора *vbc.exe*. |
| `DocumentationFile` | Необязательный параметр `String`.<br /><br /> Обрабатывает комментарии к документации в указанный XML-файл. Этот параметр переопределяет атрибут `GenerateDocumentation`. Дополнительные сведения см. в разделе [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, задача генерирует отладочную информацию и помещает ее в *PDB-файл*. Дополнительные сведения см. в разделе [-debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Необязательный параметр `String`.<br /><br /> Указывает, как задача должна сообщать о внутренних ошибках компилятора. Этот параметр может иметь следующие значения:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Если задано значение `prompt`, то при возникновении внутренней ошибки компилятора пользователю предлагается возможность отправить сведения об ошибке в корпорацию Майкрософт.<br /><br /> Если присвоено значение, `send` при возникновении внутренней ошибки компилятора задача отправляет данные об ошибке в корпорацию Майкрософт.<br /><br /> Значение по умолчанию — `none`, при котором сообщение об ошибке отправляется только в виде текста.<br /><br /> Этот параметр соответствует параметру [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) компилятора *vbc.exe*. |
| `FileAlignment` | Необязательный параметр `Int32`.<br /><br /> Задает выравнивание размеров выходного файла в байтах. Этот параметр может иметь следующие значения:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Этот параметр соответствует параметру [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) компилятора *vbc.exe*. |
| `GenerateDocumentation` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, в процессе сборки создается информация документации и помещается в XML-файл вместе с именем исполняемого файла или библиотеки, созданных задачей. Дополнительные сведения см. в разделе [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Импорт пространства имен из указанных коллекций элементов. Этот параметр соответствует параметру [-imports](/dotnet/visual-basic/reference/command-line-compiler/imports) компилятора *vbc.exe*. |
| `KeyContainer` | Необязательный параметр `String`.<br /><br /> Задает имя контейнера криптографического ключа. Этот параметр соответствует параметру [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) компилятора *vbc.exe*. |
| `KeyFile` | Необязательный параметр `String`.<br /><br /> Задает имя файла, содержащего криптографический ключ. Дополнительные сведения см. в разделе [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Необязательный параметр <xref:System.String?displayProperty=fullName>.<br /><br /> Задает используемую [версию языка](/dotnet/visual-basic/language-reference/configure-language-version) (например, 15.5). |
| `LinkResources` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Создается ссылка на ресурс .NET Framework в выходном файле. Файл ресурса не помещается в выходной файл. Этот параметр соответствует параметру [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) компилятора *vbc.exe*. |
| `MainEntryPoint` | Необязательный параметр `String`.<br /><br /> Задает класс или модуль, содержащий процедуру `Sub Main`. Этот параметр соответствует параметру [-main](/dotnet/visual-basic/reference/command-line-compiler/main) компилятора *vbc.exe*. |
| `ModuleAssemblyName` | Необязательный параметр `String`.<br /><br /> Задает сборку, частью которой будет этот модуль. |
| `NoConfig` | Необязательный параметр `Boolean`.<br /><br /> Указывает, что компилятор не должен использовать файл *vbc.rsp*. Этот параметр соответствует параметру [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) компилятора *vbc.exe*. |
| `NoLogo` | Необязательный параметр `Boolean`.<br /><br /> Если этот параметр равен `true`, отображение заголовка компилятора отключается. Этот параметр соответствует параметру [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) компилятора *vbc.exe*. |
| `NoStandardLib` | Необязательный параметр `Boolean`.<br /><br /> Указывает компилятору не ссылаться на стандартные библиотеки. Этот параметр соответствует параметру [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) компилятора *vbc.exe*. |
| `NoVBRuntimeReference` | Необязательный параметр `Boolean`.<br /><br /> Только для внутреннего использования. Если присвоено значение true, это предотвращает автоматическую ссылку на *Microsoft.VisualBasic.dll*. |
| `NoWarnings` | Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, задача отключает все предупреждения. Дополнительные сведения см. в разделе [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение`true`, разрешает оптимизацию компилятора. Этот параметр соответствует параметру [-optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) компилятора *vbc.exe*. |
| `OptionCompare` | Необязательный параметр `String`.<br /><br /> Задает способ сравнения строк. Этот параметр может иметь следующие значения:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Значение `binary` указывает на то, что в задаче используются двоичные сравнения строк. Значение `text` указывает на то, что в задаче используются текстовые сравнения строк. По умолчанию этот параметр имеет значение `binary`. Этот параметр соответствует параметру [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) компилятора *vbc.exe*. |
| `OptionExplicit` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, требуется явное объявление переменных. Этот параметр соответствует параметру [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) компилятора *vbc.exe*. |
| `OptionInfer` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, для переменных разрешено определение типа. |
| `OptionStrict` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, задача применяет строгую семантику типа и ограничивает неявное преобразование типов. Этот параметр соответствует параметру [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) компилятора *vbc.exe*. |
| `OptionStrictType` | Необязательный параметр `String`.<br /><br /> Указывает, какая строгая семантика типа генерирует предупреждение. В настоящее время поддерживается только custom. Этот параметр соответствует параметру [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) компилятора *vbc.exe*. |
| `OutputAssembly` | Необязательный выходной параметр `String`.<br /><br /> Задает имя выходного файла. Этот параметр соответствует параметру [-out](/dotnet/visual-basic/reference/command-line-compiler/out) компилятора *vbc.exe*. |
| `Platform` | Необязательный параметр `String`.<br /><br /> Указывает целевую платформу процессора для выходного файла. Этот параметр может иметь значение `x86`, `x64`, `Itanium` или `anycpu`. Значение по умолчанию — `anycpu`. Этот параметр соответствует параметру [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) компилятора *vbc.exe*. |
| `References` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Вызывает импорт задачей информации об открытых типах из заданных элементов в текущий проект. Этот параметр соответствует параметру [-reference](/dotnet/visual-basic/reference/command-line-compiler/reference) компилятора *vbc.exe*. |
| `RemoveIntegerChecks` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, отключает проверку переполнения для целочисленных значений. Значение по умолчанию — `false`. Этот параметр соответствует параметру [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) компилятора *vbc.exe*. |
| `Resources` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Внедряет ресурс .NET Framework в выходной файл. Этот параметр соответствует параметру [-resource](/dotnet/visual-basic/reference/command-line-compiler/resource) компилятора *vbc.exe*. |
| `ResponseFiles` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает файл ответов, содержащий команды для этой задачи. Этот параметр соответствует параметру [@ (указание файла ответа)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) компилятора *vbc.exe*. |
| `RootNamespace` | Необязательный параметр `String`.<br /><br /> Задает корневое пространство имен для всех объявлений типов. Этот параметр соответствует параметру [-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) компилятора *vbc.exe*. |
| `SdkPath` | Необязательный параметр `String`.<br /><br /> Задает расположение библиотек *mscorlib.dll* и *microsoft.visualbasic.dll*. Этот параметр соответствует параметру [-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) компилятора *vbc.exe*. |
| `Sources` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает один или несколько исходных файлов Visual Basic. |
| `TargetCompactFramework` | Необязательный параметр `Boolean`.<br /><br /> Если `true`, задача предназначена для .NET Compact Framework. Этот параметр соответствует параметру [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) компилятора *vbc.exe*. |
| `TargetType` | Необязательный параметр `String`.<br /><br /> Задает формат выходного файла. Этот параметр может принимать одно из следующих значений: `library` (создается библиотека кода), `exe` (создается консольное приложение), `module` (создается модуль) или `winexe` (создается программа Windows). Значение по умолчанию — `library`. Этот параметр соответствует параметру [-target](/dotnet/visual-basic/reference/command-line-compiler/target) компилятора *vbc.exe*. |
| `Timeout` | Необязательный параметр `Int32`.<br /><br /> Задает промежуток времени в миллисекундах, после которого исполняемый файл задачи прекращается. Значение по умолчанию — `Int.MaxValue`. Оно указывает, что период ожидания отсутствует. |
| `ToolPath` | Необязательный параметр `String`.<br /><br /> Указывает расположение, из которого задача будет загружать базовый исполняемый файл (*vbc.exe*). Если этот параметр не задан, задача использует путь установки пакета SDK, соответствующий версии платформы, на которой выполняется MSBuild. |
| `TreatWarningsAsErrors` | Необязательный параметр `Boolean`.<br /><br /> Если присвоено значение `true`, все предупреждения обрабатываются как ошибки. Дополнительные сведения см. в разделе [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Необязательный параметр `Boolean`.<br /><br /> Предписывает задаче использовать внутрипроцессный объект компилятора, если он доступен. Используется только в Visual Studio. |
| `Utf8Output` | Необязательный параметр `Boolean`.<br /><br /> Регистрирует выходные данные компилятора в кодировке UTF-8. Этот параметр соответствует параметру [-utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) компилятора *vbc.exe*. |
| `Verbosity` | Необязательный параметр `String`.<br /><br /> Задает уровень детализации выходных данных компилятора. Уровень детализации может быть `Quiet`, `Normal` (по умолчанию) или `Verbose`. |
| `WarningsAsErrors` | Необязательный параметр `String`.<br /><br /> Задает список предупреждений, которые следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Этот параметр переопределяет параметр `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Необязательный параметр `String`.<br /><br /> Задает список предупреждений, которые не следует обрабатывать как ошибки. Дополнительные сведения см. в разделе [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Этот параметр имеет смысл только в том случае, если для параметра `TreatWarningsAsErrors` задано значение `true`. |
| `Win32Icon` | Необязательный параметр `String`.<br /><br /> Вставляет файл *ICO* в сборку, которая придает выходному файлу необходимый вид в **проводнике**. Этот параметр соответствует параметру [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) компилятора *vbc.exe*. |
| `Win32Resources` | Необязательный параметр `String`.<br /><br /> Вставляет файл ресурсов Win32 (*RES-файл*) в выходной файл. Этот параметр соответствует параметру [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) компилятора *vbc.exe*. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Пример

 В следующем примере компилируется проект Visual Basic.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>См. также

- [Компилятор Visual Basic с интерфейсом командной строки](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
