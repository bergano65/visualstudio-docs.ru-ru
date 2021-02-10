---
title: Настройка анализа покрытия кода
description: Сведения о том, как использовать атрибут ExcludeFromCodeCoverageAttribute для исключения кода теста из результатов покрытия. Вы можете включить сборки, не входящие в состав вашего решения.
ms.custom: SEO-VS-2020
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 65044baf78e6f49e35f011a4853111063e82a192
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964411"
---
# <a name="customize-code-coverage-analysis"></a>Настройка анализа объема протестированного кода

По умолчанию средство объема протестированного кода анализирует все сборки решения, загруженные во время модульных тестов. Рекомендуется оставить настройки по умолчанию, поскольку они подходят для большинства случаев. Дополнительные сведения см. в разделе [Использование покрытия кода для определения объема протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Чтобы исключить тестовый код из результатов объема протестированного кода и учитывать только код приложения, добавьте атрибут <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> в тестовый класс.

Чтобы включить сборки, не входящие в решение, получите *PDB*-файлы для этих сборок и скопируйте их в ту же папку, что и *DLL*-файлы сборки.

## <a name="run-settings-file"></a>Файл параметров запуска

[Файл параметров запуска](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) — это файл конфигурации, используемый средствами модульного тестирования. Дополнительные параметры объема протестированного кода определяются в *RUNSETTINGS*-файле.

Чтобы настроить объем протестированного кода, выполните следующие действия:

1. Добавьте файл параметров запуска в решение. В **обозревателе решений** в контекстном меню выберите **Добавить** > **Новый элемент** и **XML-файл**. Сохраните файл с именем, похожим на *CodeCoverage.runsettings*.

2. Добавьте содержимое из файла примера в конце этой статьи, а затем настройте его в соответствии с собственными требованиями, как описано в следующих разделах.

::: moniker range="vs-2017"

3. Чтобы выбрать файл параметров запуска, в меню **Тест** выберите **Параметры тестирования** > **Выбрать файл параметров теста**. Чтобы указать файл параметров запуска для запуска тестов из командной строки, см. раздел [Настройка модульных тестов](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Чтобы выбрать файл параметров запуска, в меню **Тестирование** щелкните **Выбрать файл параметров**. Чтобы указать файл параметров запуска для запуска тестов из командной строки, см. раздел [Настройка модульных тестов](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

   При выборе **Анализа объема протестированного кода** данные конфигурации считываются из файла параметров запуска.

   > [!TIP]
   > Предыдущие результаты объема протестированного кода и цвета кода не скрываются автоматически при выполнении тестов или обновлении кода.

::: moniker range="vs-2017"

Чтобы включить или отключить пользовательские параметры, выберите файл или отмените его выбор в меню **Тест**  **>Параметры тестирования**.

![Меню параметров тестирования с пользовательским файлом параметров в Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Чтобы включить или отключить пользовательские параметры, выберите файл или отмените его выбор в меню **Тестирование**.

::: moniker-end

## <a name="symbol-search-paths"></a>Пути поиска символов

Для объема протестированного кода необходимы файлы символов (*PDB*-файлы) в сборках. В случае сборок, созданных в вашем решении, файлы символов обычно предоставляются вместе с двоичными файлами, и объем протестированного кода работает автоматически. В некоторых случаях может потребоваться включить сборки, на которые указывают ссылки, в анализ объема протестированного кода. В таких случаях *PDB*-файлы могут находиться далеко от двоичных файлов, однако путь поиска символов можно указать в *RUNSETTINGS*-файле.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Разрешение символов может занять время, особенно при использовании удаленного расположения файлов со множеством сборок. Поэтому рекомендуется скопировать *PDB*-файлы в то же локальное расположение, в котором находятся двоичные файлы (*DLL* и *EXE*).

## <a name="include-or-exclude-assemblies-and-members"></a>Включение или исключение сборок и членов

Вы можете включать сборки или определенные типы и члены в анализ объема протестированного кода или исключать их из него. Если раздел **Include** пуст или отсутствует, включаются все загруженные сборки, с которыми связаны PDB-файлы. Если сборка или член соответствует предложению в разделе **Exclude**, то они исключаются из анализа объема протестированного кода. Раздел **Exclude** имеет приоритет над разделом **Include**: если сборка указана как в разделе **Include**, так и в разделе **Exclude**, она не включается в анализ объема протестированного кода.

Например, в следующем коде XML исключается одна сборка, указанная по имени:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

В следующем примере указывается, что в анализ объема протестированного кода должна включаться только одна сборка:

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

В приведенной ниже таблице показаны различные способы сопоставления сборок и членов для включения в анализ объема протестированного кода или исключения из него.

| Элемент XML | Соответствие |
| - | - |
| ModulePath | Сопоставление со сборками, указанными по имени или пути к файлу. |
| CompanyName | Сопоставление сборок по атрибуту **Company**. |
| PublicKeyToken | Сопоставление подписанных сборок по токену открытого ключа. |
| Source | Сопоставление элементов по имени пути к файлу исходного кода, в котором они определены. |
| Атрибут | Сопоставление элементов, у которых имеется указанный атрибут. Укажите полное имя атрибута, например `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`.<br/><br/>Если исключить атрибут <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute>, код, использующий языковые функции, такие как `async`, `await`, `yield return`, и автоматические реализуемые свойства, исключается из анализа объема протестированного кода. Чтобы исключить созданный код, исключите только атрибут <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. |
| Функция | Сопоставление процедур, функций или методов по полному имени, включая список параметров. Возможно также сопоставление с частью имени с помощью [регулярного выражения](#regular-expressions).<br/><br/>Примеры<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)` (C++) |

### <a name="regular-expressions"></a>Регулярные выражения

Для включения и исключения узлов используются регулярные выражения, которые не совпадают с подстановочными знаками. Все соответствия не учитывают регистр. Ниже приведено несколько примеров.

- **.\*** соответствует строке любых символов

- **\\.** соответствует точке (".")

- **\\(   \\)** соответствует круглым скобкам "( )"

- **\\\\** соответствует разделителю пути к файлу "\\"

- **^** соответствует началу строки

- **$** соответствует концу строки

В следующем коде XML показано, как включать и исключать определенные сборки с помощью регулярных выражений:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

В следующем коде XML показано, как включать и исключать определенные функции с помощью регулярных выражений:

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

> [!WARNING]
> Если в регулярном выражении есть ошибка, например круглые скобки без escape-последовательности или непарные круглые скобки, то анализ объема протестированного кода не выполняется.

Дополнительные сведения о регулярных выражениях см. в статье [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>Пример RUNSETTINGS-файла

Скопируйте этот код и измените его в соответствии с требованиями.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>См. также

- [Настройка модульных тестов с помощью файла параметров запуска](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Использование покрытия кода для определения объема протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Модульное тестирование кода](../test/unit-test-your-code.md)
