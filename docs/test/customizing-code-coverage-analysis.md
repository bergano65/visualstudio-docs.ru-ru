---
title: "Настройка анализа покрытия кода | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6337c35-acae-4c5f-b5d9-ac5ff687ef18
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "mlearned"
manager: "douge"
---
# Настройка анализа покрытия кода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

По умолчанию средство покрытия кода Visual Studio анализирует все сборки решения \(EXE\/DLL\), загруженные во время модульных тестов.  Рекомендуется оставить настройки по умолчанию, поскольку они подходят для большинства случаев.  Дополнительные сведения см. в разделе [Использование покрытия кода для определения объема протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Перед настройкой поведения покрытия кода рассмотрите некоторые альтернативные решения.  
  
-   *Как исключить тестовый код из результатов кода покрытия и включить только код приложения.*  
  
     Добавьте `ExcludeFromCodeCoverage Attribute` в свой тестовый класс.  
  
-   *Как включить сборки, которые не являются частью решения.*  
  
     Получите PDB\-файлы для этих сборок и скопируйте их в ту же папку, что и DLL\-файлы сборки.  
  
 Для настройки поведения покрытия кода скопируйте [пример в конце этого раздела](#sample) и добавьте его к решению, используя расширение файла RUNSETTINGS.  Измените его в соответствии с собственными требованиями, а затем в меню **Тест** щелкните **Параметры тестирования** и выберите **Выбрать файл параметров теста**.  В оставшейся части этого раздела подробно описывается данная процедура.  
  
## RUNSETTINGS\-файл  
 Дополнительные параметры покрытия кода определяются в RUNSETTINGS\-файле.  Это файл конфигурации, используемый средствами модульного тестирования.  Рекомендуется скопировать [пример в конце этого раздела](#sample) и изменить его в соответствии с собственными требованиями.  
  
-   *Что произошло с TESTSETTINGS\-файлом, который использовался в Visual Studio 2010?*  
  
     В Visual Studio 2010 TESTSETTINGS\-файл применяется только к модульным тестам на основе платформы MSTest.  В Visual Studio 2012 средства тестирования применяются не только к MSTest, но и к другим платформам, таким как NUnit и xUnit.  net.  Эти платформы не поддерживают TESTSETTINGS\-файл.  С помощью RUNSETTINGS\-файла средства тестирования можно настроить таким образом, чтобы они работали на всех платформах тестирования.  
  
 Для настройки покрытия кода необходимо добавить RUNSETTINGS\-файл к решению.  
  
1.  Добавьте XML\-файл в качестве элемента решения с расширением `RUNSETTINGS`.  
  
     В обозревателе решений в контекстном меню нажмите кнопку **Добавить**, щелкните **Создать элемент** и выберите **XML\-файл**.  Сохраните файл с именем, заканчивающимся на `CodeCoverage.runsettings`  
  
2.  Добавьте содержимое, предоставленное в примере в конце данного раздела, а затем настройте его в соответствии с собственными требованиями, как описано в следующих разделах.  
  
3.  В меню **Тест** выберите **Параметры тестирования**, щелкните **Выбрать файл параметров теста** и выберите файл.  
  
4.  Теперь при выполнении команды **Анализ покрытия кода** данный `RUNSETTINGS-`файл будет управлять его поведением.  Не забудьте, что покрытие кода необходимо выполнить еще раз, поскольку предыдущие результаты покрытия и цвета кода не скрываются автоматически при выполнении тестов или обновлении кода.  
  
5.  Чтобы включить или отключить пользовательские параметры, выберите файл или отмените его выбор в разделе **Параметры тестирования** в меню **Тест**.  
  
 ![Меню параметров тестирования с пользовательским файлом параметров](../test/media/codecoverage-settingsfile.png "CodeCoverage\-settingsFile")  
  
 Другие аспекты модульных тестов можно настроить в том же RUNSETTINGS\-файле.  Дополнительные сведения см. в разделе [Модульное тестирование кода](../test/unit-test-your-code.md).  
  
### Указание путей поиска символов  
 Для покрытия кода необходимо наличие символов \(PDB\-файлов\) в сборках.  В случае сборок, созданных в вашем решении, файлы символов обычно предоставляются вместе с двоичными файлами, и покрытие кода работает автоматически.  Однако в некоторых случаях может потребоваться включить сборки, на которые указывают ссылки, в анализ покрытия кода.  В таких случаях PDB\-файлы могут находиться далеко от двоичных файлов, однако путь поиска символов можно указать в RUNSETTINGS\-файле.  
  
```xml  
<SymbolSearchPaths>                
      <Path>\\mybuildshare\builds\ProjectX</Path>  
      <!--More paths if required-->  
</SymbolSearchPaths>  
  
```  
  
> [!WARNING]
>  Разрешение символов может занять время, особенно при использовании удаленного расположения файлов со множеством сборок.  Поэтому рекомендуется скопировать удаленные PDB\-файлы в то же локальное расположение, в котором находятся двоичные файлы \(DLL и EXE\).  
  
### Исключение и включение  
 Можно исключить указанные сборки из анализа покрытия кода.  Например:  
  
```minterastlib  
<ModulePaths>  
  <Exclude>  
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Exclude>  
</ModulePaths>  
```  
  
 Либо можно указать, какие сборки должны быть включены.  Данный подход имеет недостаток — при добавлении дополнительных сборок в решение их также необходимо добавить в список.  
  
```minterastlib  
<ModulePaths>  
  <Include>  
   <ModulePath>Fabrikam.Math.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Include>  
</ModulePaths>  
```  
  
 Если параметр `<Include>` пуст, то в обработку покрытия кода будут включены все сборки \(DLL\- и EXE\-файлы\), которые уже загружены и для которых можно найти файлы **.pdb**, за исключением элементов, которые соответствуют предложению в списке `<Exclude>`.  
  
 `Include` обрабатывается перед `Exclude`.  
  
### Регулярные выражения  
 Узлы включения и исключения используют регулярные выражения.  Дополнительные сведения см. в разделе [Использование регулярных выражений в Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  Регулярные выражения не равнозначны подстановочным знакам.  В частности:  
  
1.  **.\*** соответствует строке любых символов  
  
2.  **\\.** соответствует точке ".".  
  
3.  **\\\(   \\\)** соответствует круглым скобкам "\( \)".  
  
4.  **\\\\** соответствует разделителю пути к файлу "\\".  
  
5.  **^** соответствует началу строки  
  
6.  **$** соответствует концу строки  
  
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
>  Если в регулярном выражении есть ошибка, например круглые скобки без escape\-последовательности или непарные круглые скобки, то анализ покрытия кода не выполняется.  
  
### Другие способы включения или исключения элементов  
 См. [пример в конце этого раздела](#sample).  
  
-   `ModulePath` — сборки, указанные путем к файлу сборки.  
  
-   `CompanyName` — сопоставление сборок по атрибуту Company.  
  
-   `PublicKeyToken` — сопоставление подписанных сборок по токену открытого ключа.  Например, чтобы сопоставить все компоненты и расширения Visual Studio, используйте `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>`.  
  
-   `Source` — сопоставление элементов по имени пути к файлу исходного кода, в котором они определены.  
  
-   `Attribute` — сопоставление элементов с определенным атрибутом.  Укажите полное имя атрибута, включая Attribute в конце имени.  
  
-   `Function` — сопоставление процедур, функций или методов по полному имени.  
  
 **Соответствие имени функции**  
  
 Ваше регулярное выражение должно соответствовать полному имени функции, включая пространство имен, имя класса, имя метода и список параметров.  Например:  
  
-   C\# или Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`  
  
-   C\+\+: `Fabrikam::Math::LocalMath::SquareRoot(double)`  
  
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
  
## Определение RUNSETTINGS\-файлов при выполнении тестов  
  
### Настройка RUNSETTINGS\-файла в тестах Visual Studio  
 В меню **Тест** выберите **Параметры тестирования**, щелкните **Выбрать файл параметров теста** и выберите RUNSETTINGS\-файл.  В меню "Параметры тестирования" отобразится файл, который можно выбрать или отменить.  Если RUNSETTINGS\-файл выбран, он применяется при каждом выполнении команды **Анализ покрытия кода**.  
  
### Настройка параметров запуска в тесте командной строки  
 Для выполнения тестов из командной строки используйте vstest.console.exe.  Файл параметров является параметром этой служебной программы.  Дополнительные сведения см. в файле [Использование VSTest.console из командной строки](/devops-test-docs/test/using-vstest-console-from-the-command-line).  
  
1.  Запустите командную строку разработчика Visual Studio.  
  
     В меню **Пуск** Windows последовательно щелкните **Все программы**, **Microsoft Visual Studio**, **Инструменты Visual Studio**, **Командная строка разработчика**.  
  
2.  Выполните следующий файл.  
  
     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`  
  
### Настройка параметров запуска в определении сборки  
 Можно получить данные о покрытии кода из командной сборки.  
  
 ![Задание параметров запуска в определении построения](../test/media/codecoverage-buildrunsettings.png "CodeCoverage\-buildRunsettings")  
  
1.  Убедитесь, что RUNSETTINGS\-файл возвращен.  
  
2.  В Team Explorer откройте меню **Сборки**, а затем добавьте или измените определение сборки.  
  
3.  На странице **Процесс** разверните **Автоматизированные тесты**, **Исходный код теста**, **Параметры запуска**.  Выберите файл **.runsettings**.  
  
    -   *Вместо параметра **Исходный код теста** появляется параметр **Сборка теста**.  При попытке настроить поле **Параметры запуска** для выбора доступны только TESTSETTINGS\-файлы.*  
  
         В разделе **Автоматизированные тесты** щелкните **Сборка теста** и выберите **\[...\]** в конце строки.  В диалоговом окне **Добавить\/изменить тестовый запуск** установите для параметра **Средство выполнения тестов** значение **Средство выполнения тестов Visual Studio**.  
  
 Результаты отображаются в сводном разделе отчета о сборке.  
  
##  <a name="sample"></a> Пример RUNSETTINGS\-файла  
 Скопируйте этот код и измените его в соответствии с собственными требованиями.  Это RUNSETTINGS\-файл по умолчанию.  
  
 \(Сведения о других вариантах использования RUNSETTINGS\-файла см. в разделе [Настройка модульных тестов с помощью файла .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).\)  
  
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
Each element in the list is a regular expression (ECMAScript syntax). See http://msdn.microsoft.com/library/2k3te2cs.aspx.  
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
                <!—Don't forget "Attribute" at the end of the name -->  
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
  
## См. также  
 [Использование покрытия кода для определения объема протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)   
 [Модульное тестирование кода](../test/unit-test-your-code.md)