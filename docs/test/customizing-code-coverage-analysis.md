---
title: Настройка анализа покрытия кода
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 09af57ca64524dafa506d57d486e9385a4c35a93
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054949"
---
# <a name="customize-code-coverage-analysis"></a>Настройка анализа объема протестированного кода

По умолчанию средство объема протестированного кода анализирует все сборки решения, загруженные во время модульных тестов. Рекомендуется оставить настройки по умолчанию, поскольку они подходят для большинства случаев. Дополнительные сведения см. в разделе [Использование покрытия кода для определения объема протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Чтобы исключить тестовый код из результатов объема протестированного кода и учитывать только код приложения, добавьте атрибут <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> в тестовый класс.

Чтобы включить сборки, не входящие в решение, получите *PDB*-файлы для этих сборок и скопируйте их в ту же папку, что и *DLL*-файлы сборки.

## <a name="run-settings-file"></a>Файл параметров запуска

[Файл параметров запуска](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) — это файл конфигурации, используемый средствами модульного тестирования. Дополнительные параметры объема протестированного кода определяются в *RUNSETTINGS*-файле.

Чтобы настроить объем протестированного кода, выполните следующие действия:

1. Добавьте файл параметров запуска в решение. В **обозревателе решений** в контекстном меню выберите **Добавить** > **Новый элемент** и **XML-файл**. Сохраните файл с именем, похожим на *CodeCoverage.runsettings*.

1. Добавьте содержимое из файла примера в конце этой статьи, а затем настройте его в соответствии с собственными требованиями, как описано в следующих разделах.

1. Чтобы выбрать файл параметров запуска, в меню **Тест** выберите **Параметры тестирования** > **Выбрать файл параметров теста**. Чтобы указать файл параметров запуска для запуска тестов из командной строки или в рабочем процессе сборки, см. раздел [Настройка модульных тестов с помощью файла *.runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   При выборе **Анализа объема протестированного кода** данные конфигурации считываются из файла параметров запуска.

   > [!TIP]
   > Предыдущие результаты объема протестированного кода и цвета кода не скрываются автоматически при выполнении тестов или обновлении кода.

Чтобы включить или отключить пользовательские параметры, выберите файл или отмените его выбор в разделе **Тест** > **Параметры тестирования**.

![Меню параметров тестирования с пользовательским файлом параметров](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Указание путей поиска символов

Для объема протестированного кода необходимы файлы символов (*PDB*-файлы) в сборках. В случае сборок, созданных в вашем решении, файлы символов обычно предоставляются вместе с двоичными файлами, и объем протестированного кода работает автоматически. Однако в некоторых случаях может потребоваться включить сборки, на которые указывают ссылки, в анализ покрытия кода. В таких случаях *PDB*-файлы могут находиться далеко от двоичных файлов, однако путь поиска символов можно указать в *RUNSETTINGS*-файле.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Разрешение символов может занять время, особенно при использовании удаленного расположения файлов со множеством сборок. Поэтому рекомендуется скопировать *PDB*-файлы в то же локальное расположение, в котором находятся двоичные файлы (*DLL* и *EXE*).

### <a name="exclude-and-include"></a>Включение и исключение

Можно исключить указанные сборки из анализа покрытия кода. Например:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Либо можно указать, какие сборки должны быть включены. Данный подход имеет недостаток — при добавлении дополнительных сборок в решение их также необходимо добавить в список.

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Если параметр **include** пуст, то в обработку объема протестированного кода будут включены все сборки, которые уже загружены и для которых можно найти файлы *PDB*. В объем протестированного кода не включаются элементы, которые соответствуют предложению в списке **Exclude**.

**Включение** обрабатывается до **исключения**.

### <a name="regular-expressions"></a>Регулярные выражения

Узлы включения и исключения используют регулярные выражения. Дополнительные сведения см. в статье [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Регулярные выражения не равнозначны подстановочным знакам. В частности:

- **.\\*** соответствует строке любых символов

- **\\.** соответствует точке (".")

- **\\(   \\)** соответствует круглым скобкам "( )"

- **\\\\** соответствует разделителю пути к файлу "\\"

- **^** соответствует началу строки

- **$** соответствует концу строки

Все соответствия не учитывают регистр.

Например:

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

> [!WARNING]
> Если в регулярном выражении есть ошибка, например круглые скобки без escape-последовательности или непарные круглые скобки, то анализ объема протестированного кода не выполняется.

### <a name="other-ways-to-include-or-exclude-elements"></a>Другие способы включения или исключения элементов

- **ModulePath** — сопоставление сборок, указанные путем к файлу сборки.

- **CompanyName** — сопоставление сборок по атрибуту **Company**.

- **PublicKeyToken** — сопоставление подписанных сборок по токену открытого ключа.

- **Source** — сопоставление элементов по имени пути к файлу исходного кода, в котором они определены.

- **Attribute** — сопоставление элементов с определенным атрибутом. Укажите полное имя атрибута и укажите Attribute в конце имени.

- **Function** — сопоставление процедур, функций или методов по полному имени. Чтобы сопоставить имя функции, ваше регулярное выражение должно соответствовать полному имени функции, включая пространство имен, имя класса, имя метода и список параметров. Пример:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

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
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
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
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
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
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
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