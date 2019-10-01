---
title: Настройка модульных тестов с помощью RUNSETTINGS-файла
ms.date: 06/14/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 25d0f49939a42d9a9b8cc56f03ed37ab83aa98f2
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251830"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Настройка модульных тестов с помощью файла *.runsettings*

Модульные тесты в Visual Studio можно настроить с помощью файла *.runsettings*. Например, можно изменить версию платформы .NET, на которой выполняются тесты, каталог для результатов теста и данные, собранные во время тестового запуска.

Файлы параметров запуска являются необязательными. Если вам не требуется специальная конфигурация, файл *.runsettings* не нужен. Чаще всего файл *.runsettings* используют для настройки [анализа объема протестированного кода](../test/customizing-code-coverage-analysis.md).

## <a name="specify-a-run-settings-file"></a>Указание файла параметров запуска

Файлы параметров запуска можно использовать для настройки тестов, которые запускаются из [командной строки](vstest-console-options.md), в интегрированной среде разработки или в [рабочем процессе сборки](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts) с помощью Azure Test Plans или Team Foundation Server (TFS).

### <a name="ide"></a>IDE

::: moniker range="vs-2017"

Чтобы указать файл параметров запуска в интегрированной среде разработки, выберите **Тест** > **Параметры тестирования** > **Выбрать файл параметров тестирования**, а затем выберите файл *.runsettings*.

![Выбор файла параметров тестирования в Visual Studio 2017](media/select-test-settings-file.png)

В меню "Параметры тестирования" появится файл, который можно выбрать или отменить выбор. Если файл параметров запуска выбран, он применяется при каждом выборе функции **Анализ объема протестированного кода**.

::: moniker-end

::: moniker range=">=vs-2019"

Чтобы указать файл параметров запуска в интегрированной среде разработки, в **обозревателе тестов** щелкните стрелку на кнопке **Параметры**, а затем выберите пункт **Выбрать файл параметров**. Найдите и выберите файл *.runsettings*.

![Выбор файла параметров тестирования в Visual Studio 2019](media/vs-2019/select-test-settings-file.png)

В обозревателе тестов в меню "Параметры" появится файл, который можно выбрать или отменить выбор. Если файл параметров запуска выбран, он применяется при каждом выборе функции **Анализ объема протестированного кода**.

::: moniker-end

### <a name="command-line"></a>Командная строка

Для запуска тестов из командной строки используйте *vstest.console.exe* и укажите файл параметров с помощью параметра **/Settings**.

1. Запустите командную строку разработчика Visual Studio.

   ::: moniker range="vs-2017"

   В ОС Windows в меню **Пуск** выберите **Visual Studio 2017** > **Командная строка разработчика для VS 2017**.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   В ОС Windows в меню **Пуск** выберите **Visual Studio 2019** > **Командная строка разработчика для VS 2019**.

   ::: moniker-end

2. Введите команду, подобную следующей:

   ```cmd
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings
   ```

   или

   ```cmd
   vstest.console.exe --settings:test.runsettings test.dll
   ```

Дополнительные сведения см. в статье [Параметры командной строки для VSTest.Console.exe](vstest-console-options.md).

## <a name="customize-tests"></a>Настройка тестов

Чтобы настроить тесты с использованием файла *.runsettings*, выполните следующие действия.

1. Добавьте XML-файл в свое решение Visual Studio и сохраните его с именем *test.runsettings*.

   > [!TIP]
   > Имя файла не имеет значения, если вы используете расширение *.runsettings*.

2. Замените содержимое файла XML в следующем примере и при необходимости настройте его.

::: moniker range="vs-2017"

3. В меню **Тест** щелкните **Параметры тестирования** > **Выбрать файл параметров теста**. Перейдите к созданному вами файлу *.runsettings*, а затем нажмите **ОК**.

::: moniker-end

::: moniker range=">=vs-2019"

3. Чтобы выбрать файл параметров запуска, в **обозревателе тестов** щелкните стрелку на кнопке **Параметры**, а затем выберите пункт **Выбрать файл параметров**. Перейдите к созданному вами файлу *.runsettings*, а затем нажмите **ОК**.

::: moniker-end

   > [!TIP]
   > Можно создать в решении несколько файлов *.runsettings* файлов и при необходимости выбирать один из них в качестве действующего файла параметров тестирования.

## <a name="example-runsettings-file"></a>Пример файла *.runsettings*

Следующий XML-код представляет содержимое обычного файла *.runsettings*. Каждый элемент этого файла необязателен, так как все они имеют значения по умолчанию.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RunSettings>
  <!-- Configurations that affect the Test Framework -->
  <RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <!-- Path relative to directory that contains .runsettings file-->
    <ResultsDirectory>.\TestResults</ResultsDirectory>

    <!-- x86 or x64 -->
    <!-- You can also change it from the test settings menu; choose "Processor Architecture for AnyCPU Projects" -->
    <TargetPlatform>x86</TargetPlatform>

    <!-- Framework35 | [Framework40] | Framework45 -->
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>

    <!-- Path to Test Adapters -->
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>

    <!-- TestSessionTimeout was introduced in Visual Studio 2017 version 15.5 -->
    <!-- Specify timeout in milliseconds. A valid value should be greater than 0 -->
    <TestSessionTimeout>10000</TestSessionTimeout>
  </RunConfiguration>

  <!-- Configurations for data collectors -->
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
            <ModulePaths>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- We recommend you do not change the following values: -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>

      <DataCollector uri="datacollector://microsoft/VideoRecorder/1.0" assemblyQualifiedName="Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder.VideoRecorderDataCollector, Microsoft.VisualStudio.TestTools.DataCollection.VideoRecorder, Version=15.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" friendlyName="Screen and Voice Recorder">
        <!--Video data collector was introduced in Visual Studio 2017 version 15.5 -->
        <Configuration>
           <!-- Change to "false" to only add video attachments to failed tests -->
          <MediaRecorder sendRecordedMediaForPassedTestCase="true" xmlns="" />
        </Configuration>
      </DataCollector>

    </DataCollectors>
  </DataCollectionRunSettings>

  <!-- Parameters used by tests at run time -->
  <TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
  </TestRunParameters>

  <!-- Adapter Specific sections -->

  <!-- MSTest adapter -->
  <MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
  </MSTest>

</RunSettings>
```

## <a name="elements-of-a-runsettings-file"></a>Элементы файла *.runsettings*

В последующих разделах подробно описаны элементы файла *.runsettings*.

### <a name="run-configuration"></a>Конфигурация запуска

```xml
<RunConfiguration>
    <MaxCpuCount>1</MaxCpuCount>
    <ResultsDirectory>.\TestResults</ResultsDirectory>
    <TargetPlatform>x86</TargetPlatform>
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>
    <TestSessionTimeout>10000</TestSessionTimeout>
</RunConfiguration>
```

Элемент **RunConfiguration** может содержать следующие элементы:

|Узел|По умолчанию|Значения|
|-|-|-|
|**ResultsDirectory**||Каталог для сохранения результатов тестов.|
|**TargetFrameworkVersion**|Framework40|`FrameworkCore10` для источников .NET Core, `FrameworkUap10` для источников на основе UWP, `Framework45` для .NET Framework 4.5 и более поздней версии, `Framework40` для .NET Framework 4.0 и `Framework35` для .NET Framework 3.5.<br /><br />Этот параметр указывает, какая версия платформы модульных тестов используется для поиска и выполнения тестов. Эта версия может отличаться от версии платформы .NET, указанной в свойствах сборки проекта модульного теста.<br /><br />Если опустить элемент `TargetFrameworkVersion` в файле *.runsettings*, платформа автоматически определит версию .NET на основе двоичных файлов сборки.|
|**TargetPlatform**|x86|x86, x64|
|**TreatTestAdapterErrorsAsWarnings**|false|false, true|
|**TestAdaptersPaths**||Один или несколько путей к каталогу, где находятся адаптеры TestAdapters|
|**MaxCpuCount**|1|Этот параметр управляет степенью параллелизма при выполнении тестов при запуске модульных тестов, используя доступные ядра на компьютере. Модуль выполнения тестов запускается как отдельный процесс на каждом доступном ядре и дает каждому ядру контейнер с запускаемыми тестами. Контейнером может быть сборка, библиотека DLL или соответствующий артефакт. Тестовый контейнер — это модуль, работающий по расписанию. В каждом контейнере тесты запускаются в соответствии с платформой тестов. Если контейнеров много, то после того как процессы завершают выполнение тестов в контейнере, им предоставляются следующие доступные контейнеры.<br /><br />MaxCpuCount может быть:<br /><br />n, где 1 < n < числа ядер: будет запущено до n процессов;<br /><br />n, где n равно любому другому значению: число запускаемых процессов может достигать числа доступных ядер на компьютере.|
|**TestSessionTimeout**||Дает пользователям возможность завершить сеанс тестирования, если его длительность превышает заданный промежуток времени. Задав время ожидания, вы обеспечите надлежащее использование ресурсов и ограничите выполнение сеансов тестирования определенным периодом. Этот параметр доступен в **Visual Studio 2017 версии 15.5** и более поздних версий.|

### <a name="diagnostic-data-adapters-data-collectors"></a>Адаптеры диагностических данных (сборщики данных)

Элемент **DataCollectors** задает параметры адаптеров диагностических данных. Адаптеры диагностических данных собирают дополнительные сведения о среде и тестируемом приложении. Для каждого адаптера заданы параметры по умолчанию; указывать параметры следует, только если вы не хотите использовать параметры по умолчанию.

#### <a name="code-coverage-adapter"></a>Адаптер покрытия кода

```xml
<CodeCoverage>
    <ModulePaths>
        <Exclude>
            <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
        </Exclude>
    </ModulePaths>

    <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
    <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
    <CollectFromChildProcesses>True</CollectFromChildProcesses>
    <CollectAspDotNet>False</CollectAspDotNet>
</CodeCoverage>
```

Сборщик данных о покрытии кода создает журнал с указанием того, какие части кода приложения были включены в тест. Дополнительные сведения о настройке параметров объема протестированного кода см. в разделе [Настройка анализа объема протестированного кода](../test/customizing-code-coverage-analysis.md).

#### <a name="video-data-collector"></a>Сборщик видеоданных

Сборщик видеоданных захватывает запись экрана при выполнении тестов. Эта запись полезна для устранения неполадок тестов пользовательского интерфейса. Сборщик видеоданных предусмотрен в **Visual Studio 2017 версии 15.5** и более поздних версий.

Для настройки любого другого типа адаптеров диагностических данных используйте [файл параметров тестирования](../test/collect-diagnostic-information-using-test-settings.md).

### <a name="testrunparameters"></a>TestRunParameters

```xml
<TestRunParameters>
    <Parameter name="webAppUrl" value="http://localhost" />
    <Parameter name="webAppUserName" value="Admin" />
    <Parameter name="webAppPassword" value="Password" />
</TestRunParameters>
```

Параметры тестового запуска предоставляют способ определения переменных и значений, доступных для тестов во время выполнения. Обращайтесь к параметрам с помощью свойства <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.Properties%2A?displayProperty=nameWithType>:

```csharp
[TestMethod]
public void HomePageTest()
{
    string appURL = TestContext.Properties["webAppUrl"];
}
```

Чтобы использовать параметры тестового запуска, добавьте в тестовый класс закрытое поле <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> и общедоступное свойство <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext>.

### <a name="mstest-run-settings"></a>Параметры запуска MSTest

```xml
<MSTest>
    <MapInconclusiveToFailed>True</MapInconclusiveToFailed>
    <CaptureTraceOutput>false</CaptureTraceOutput>
    <DeleteDeploymentDirectoryAfterTestRunIsComplete>False</DeleteDeploymentDirectoryAfterTestRunIsComplete>
    <DeploymentEnabled>False</DeploymentEnabled>
    <AssemblyResolution>
      <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/>
    </AssemblyResolution>
</MSTest>
```

Эти параметры относятся к адаптеру тестов, выполняющему методы теста, которые имеют атрибут <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>.

|Параметр Configuration|Значение по умолчанию|Значения|
|-|-|-|
|**ForcedLegacyMode**|false|В Visual Studio 2012 адаптер MSTest был оптимизирован для повышения скорости и масштабируемости. Некоторое поведение, в частности порядок, в котором выполняются тесты, может немного отличаться от поведения в предыдущих выпусках Visual Studio. Чтобы использовать старый адаптер теста, установите для этого параметра значение **true**.<br /><br />Например, этот параметр можно использовать при наличии файла *app.config*, указанного для модульного теста.<br /><br />Рекомендуется рассмотреть возможность рефакторинга тестов для включения возможности использования более нового адаптера.|
|**IgnoreTestImpact**|false|Функция влияния на тесты определяет приоритет тестов, на которые повлияли последние изменения, при выполнении в MSTest или из Microsoft Test Manager. Этот параметр деактивирует функцию. Дополнительные сведения см. в разделе [Какие тесты следует выполнить с момента предыдущей сборки](https://msdn.microsoft.com/library/dd286589).|
|**SettingsFile**||Здесь можно задать файл параметров тестирования для использования с адаптером MSTest. Этот файл можно также указать [из меню параметров](#ide).<br /><br />Если задано это значение, необходимо также задать для параметра **ForcedlegacyMode** значение **true**.<br /><br />`<ForcedLegacyMode>true</ForcedLegacyMode>`|
|**KeepExecutorAliveAfterLegacyRun**|false|После завершения тестового запуска MSTest завершает работу. Будет также завершен любой процесс, запущенный в рамках теста. Чтобы сохранить исполнитель тестов в активном состоянии, задайте для этого параметра значение **true**. Например, этот параметр можно использовать, чтобы браузер продолжал работать в перерывах между закодированными тестами пользовательского интерфейса.|
|**DeploymentEnabled**|true|Если установить для этого параметра значение **false**, то элементы развертывания, заданные в методе теста, не будут копироваться в каталог развертывания.|
|**CaptureTraceOutput**|true|Чтобы выполнять запись в трассировку отладки из метода теста, используйте <xref:System.Diagnostics.Trace.WriteLine%2A?displayProperty=nameWithType>.|
|**DeleteDeploymentDirectoryAfterTestRunIsComplete**|true|Чтобы сохранить каталог развертывания после завершения тестового запуска, установите для этого параметра значение **false**.|
|**MapInconclusiveToFailed**|false|Если тест завершается с неопределенным состоянием, оно обычно сопоставляется с состоянием "Пропущено" в **обозревателе тестов**. Если требуется, чтобы тесты с неопределенным результатом отображались как завершившиеся неудачно, установите для этого параметра значение **true**.|
|**InProcMode**|false|Если требуется, чтобы тесты выполнялись в одном процессе с адаптером MSTest, установите этот параметр в значение **true**. Этот параметр обеспечивает небольшое повышение производительности. Но если тест прекращается с выдачей исключения, остальные тесты выполняться не будут.|
|**AssemblyResolution**|false|При поиске и выполнении модульных тестов можно указать пути для дополнительных сборок. Например, эти пути можно использовать для сборок зависимостей, которые не находятся в том же каталоге, что и тестовая сборка. Чтобы указать путь, используйте элемент **путь к каталогу**. Пути могут содержать переменные среды.<br /><br />`<AssemblyResolution>  <Directory Path="D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|

## <a name="see-also"></a>См. также

- [Настройка тестового запуска](https://github.com/microsoft/vstest-docs/blob/master/docs/configure.md)
- [Настройка анализа объема протестированного кода](../test/customizing-code-coverage-analysis.md)
- [Задача теста Visual Studio (Azure Test Plans)](/azure/devops/pipelines/tasks/test/vstest?view=vsts)
