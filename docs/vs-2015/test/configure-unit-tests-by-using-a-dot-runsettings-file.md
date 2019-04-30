---
title: Настройка модульных тестов с помощью файла .runsettings | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7e9e4a2-5d01-4f78-b408-5be3892bd162
caps.latest.revision: 28
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e01165f12bcf3b41e4ef1279d12ce99bf8f6598f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442794"
---
# <a name="configure-unit-tests-by-using-a-runsettings-file"></a>Настройка модульных тестов с помощью файла .runsettings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Модульные тесты в Visual Studio можно настроить с помощью *RUNSETTINGS-файла. (Имя файла не имеет значения, если вы используете расширение RUNSETTINGS.) Например, можно изменить платформу .NET Framework, в которой выполняются тесты, каталог, в который отправляются результаты теста, и данные, собранные во время тестового запуска.  
  
 Если вам не требуется специальная конфигурация, *RUNSETTINGS-файл не нужен. Чаще всего он используется для настройки [объема протестированного кода](../test/customizing-code-coverage-analysis.md).  
  
> [!NOTE]
> **RUNSETTINGS-файл и TESTSETTINGS-файл**  
>   
> Существует два вида типов файлов для настройки тестов. RUNSETTINGS-файлы используются для модульных тестов. А \*TESTSETTINGS-файлы применяются для [тестирования в лабораторной среде](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901), тестов веб-производительности и нагрузки, а также для настройки некоторых типов адаптеров диагностических данных, таких как IntelliTrace и адаптеры журналов событий.  
>   
> В предыдущих выпусках Visual Studio вплоть до Visual Studio 2010 модульные тесты также настраивались с помощью *TESTSETTINGS-файлов. Это по-прежнему возможно, но тесты будут работать медленнее, чем при использовании аналогичных конфигураций в \*RUNSETTINGS-файле.  
  
## <a name="customizing-tests-with-a-runsettings-file"></a>Настройка тестов с помощью файла RUNSETTINGS  
  
1. Добавьте XML-файл в решение Visual Studio и задайте для него имя test.runsettings. (Имя файла не имеет значения, но расширением должно быть ".runsettings".)  
  
2. Замените содержимое файла [примером](#example).  
  
    Измените его в соответствии с собственными требованиями.  
  
3. В меню **Тест** щелкните **Параметры тестирования**и выберите **Выбрать файл параметров теста**.  
  
   Можно создать несколько \*RUNSETTINGS-файлов в решении и включить или отключить их в разное время с помощью меню **Параметры тестирования**.  
  
   ![Включение файла параметров запуска](../test/media/runsettings-1.png "RunSettings-1")  
  
## <a name="example"></a> Копирование файла RUNSETTINGS этого примера  
 Ниже приводится пример стандартного RUNSETTINGS-файла. Каждый элемент файла необязателен, поскольку каждое значение имеет значение по умолчанию.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<RunSettings>  
  <!-- Configurations that affect the Test Framework -->  
  <RunConfiguration>  
    <MaxCpuCount>1</MaxCpuCount>  
    <!-- Path relative to solution directory -->  
    <ResultsDirectory>.\TestResults</ResultsDirectory>  
  
    <!-- [x86] | x64    
      - You can also change it from menu Test, Test Settings, Default Processor Architecture -->  
    <TargetPlatform>x86</TargetPlatform>  
  
    <!-- Framework35 | [Framework40] | Framework45 -->  
    <TargetFrameworkVersion>Framework40</TargetFrameworkVersion>  
  
    <!-- Path to Test Adapters -->  
    <TestAdaptersPaths>%SystemDrive%\Temp\foo;%SystemDrive%\Temp\bar</TestAdaptersPaths>  
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
  
    </DataCollectors>  
  </DataCollectionRunSettings>  
  
  <!-- Parameters used by tests at runtime -->  
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
  
 RUNSETTINGS-файл также используется для настройки [объема протестированного кода](../test/customizing-code-coverage-analysis.md).  
  
 Далее в этом разделе описывается содержимое файла.  
  
## <a name="edit-your-runsettings-file"></a>Правка файла RUNSETTINGS  
 RUNSETTINGS-файл содержит следующие элементы.  
  
### <a name="test-run-configuration"></a>Конфигурация тестового запуска  
  
|Узел|По умолчанию|Значения|  
|----------|-------------|------------|  
|`ResultsDirectory`||Каталог для сохранения результатов тестов.|  
|`TargetFrameworkVersion`|Framework40|Framework35, Framework40, Framework45<br /><br /> Указывает, какая версия платформы модульных тестов используется для поиска и выполнения тестов. Эта версия может отличаться от версии платформы .NET, указанной в свойствах сборки проекта модульного теста.|  
|`TargetPlatform`|x86|x86, x64|  
|`TreatTestAdapterErrorsAsWarnings`|False|false, true|  
|`TestAdaptersPaths`||Один или несколько путей к каталогу, где находятся адаптеры TestAdapters|  
|`MaxCpuCount`|1|Управляет степенью параллелизма при выполнении тестов при запуске модульных тестов, используя доступные ядра на компьютере.  Модуль выполнения тестов запускается как отдельный процесс на каждом доступном ядре и дает каждому ядру контейнер с запускаемыми тестами, например сборку, библиотеку DLL или соответствующий артефакт.  Тестовый контейнер — это модуль, работающий по расписанию.  В каждом контейнере тесты запускаются в соответствии с платформой тестов.  Если контейнеров много, то после выполнения тестов в контейнере процессам предоставляются следующие доступные контейнеры.<br /><br /> MaxCpuCount может быть:<br /><br /> n, где 1 < = n < = числа ядер — будет запущено до n процессов.<br /><br /> n, где n = любое другое значение — число запускаемых процессов будет соответствовать числу доступных ядер на компьютере.|  
  
### <a name="diagnostic-data-adapters-data-collectors"></a>Адаптеры данных диагностики (сборщики данных)  
 Элемент `DataCollectors` определяет параметры адаптеров диагностических данных. Адаптеры диагностических данных используются для сбора дополнительных сведений о среде и тестируемом приложении. Для каждого адаптера заданы параметры по умолчанию; указывать параметры следует, только если вы не хотите использовать параметры по умолчанию.  
  
#### <a name="code-coverage-adapter"></a>Адаптер покрытия кода  
 Сборщик данных о покрытии кода создает журнал с указанием того, какие части кода приложения были включены в тест. Дополнительные сведения о настройке параметров объема протестированного кода см. в разделе [Настройка анализа покрытия кода](../test/customizing-code-coverage-analysis.md).  
  
#### <a name="other-diagnostic-data-adapters"></a>Другие адаптеры диагностических данных  
 Адаптер покрытия кода в настоящее время является единственным адаптером, который можно настроить с помощью файла параметров запуска.  
  
 Для настройки любого другого типа адаптера диагностических данных необходимо использовать файл параметров тестирования. Дополнительные сведения см. в разделе [Указание параметров тестирования для тестов Visual Studio](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901).  
  
#### <a name="testrunparameters"></a>TestRunParameters  
 TestRunParameters предоставляет способ определения переменных и значений, доступных для тестов во время выполнения.  
  
### <a name="mstest-run-settings"></a>Параметры запуска MSTest  
 Эти параметры относятся к адаптеру тестов, выполняющему методы теста, которые имеют атрибут `[TestMethod]`.  
  
|Параметр Configuration|Значение по умолчанию|Значения|  
|-------------------|-------------|------------|  
|ForcedLegacyMode|False|В Visual Studio 2012 адаптер MSTest был оптимизирован, чтобы сделать его более быстрым и более масштабируемым. Некоторое поведение, в частности порядок, в котором выполняются тесты, может немного отличаться от поведения в предыдущих выпусках Visual Studio. Установите это значение равным `true` для использования старого адаптера теста.<br /><br /> Например, это можно использовать, если имеется файл app.config, определенный для модульного теста.<br /><br /> Рекомендуется рассмотреть возможность рефакторинга тестов для включения возможности использования более нового адаптера.|  
|IgnoreTestImpact|False|Функция влияния на тесты определяет приоритет тестов, на которые повлияли последние изменения, при выполнении в MSTest или из Microsoft Test Manager. Этот параметр деактивирует функцию. Дополнительные сведения см. в разделе [как: Сбор данных для проверки тестов, которые должны быть выполнены после изменения кода](http://msdn.microsoft.com/library/2f921ea1-9bb0-4870-a30f-0521fc22cb47).|  
|SettingsFile||Здесь можно задать файл параметров тестирования для использования с адаптером теста MS. Файл параметров тестирования можно также задать с помощью меню **Тест**, **Параметры тестирования**, **Выбрать файл параметров теста**.<br /><br /> Если задано это значение, необходимо также задать для параметра **ForcedlegacyMode** значение **true**.<br /><br /> `<RunSettings>   <MSTest>     <SettingsFile>my.testsettings</SettingsFile>      <ForcedLegacyMode>true</ForcedLegacyMode>    </MSTest> </RunSettings>`|  
|KeepExecutorAliveAfterLegacyRun|False|После завершения тестового запуска MSTest завершает работу. При этом также будет завершен любой процесс, запущенный в рамках теста. Чтобы сохранить исполнитель тестов в активном состоянии, задайте для этой конфигурации значение true.<br /><br /> Например, это можно использовать, чтобы браузер продолжал работать в перерывах между закодированными тестами пользовательского интерфейса.|  
|DeploymentEnabled|true|Если установить это значение равным false, элементы развертывания, заданные в методе теста, не будут копироваться в каталог развертывания.|  
|CaptureTraceOutput|true|Можно сделать запись в трассировку отладки из метода теста с помощью Trace.WriteLine. Используя эту конфигурацию, можно отключить эти трассировки отладки.|  
|DeleteDeploymentDirectoryAfterTestRunIsComplete|true|Можно сохранить каталог развертывания после завершения тестового запуска, установив это значение равным false.|  
|MapInconclusiveToFailed|False|Если тест возвращает неопределенное состояние, оно обычно сопоставляется с состоянием "Пропущено" в обозревателе тестов. Если требуется, чтобы тесты с неопределенным результатом отображались как непройденные, используйте эту конфигурацию.|  
|InProcMode|False|Если требуется выполнить тесты в том же процессе, что и адаптер теста MS, установите это значение равным true. Этот параметр обеспечивает небольшое повышение производительности. Но если в тесте создано исключение, другие тесты выполняться не будут.|  
|AssemblyResolution|False|При поиске и выполнении модульных тестов можно указать пути для дополнительных сборок.  Эти пути можно использовать, например, для сборок зависимостей, которые не находятся в том же каталоге, что и тестовая сборка.  Чтобы указать путь, используйте элемент "Путь к каталогу".  Пути могут содержать переменные окружения.<br /><br /> `<AssemblyResolution>  <Directory Path>"D:\myfolder\bin\" includeSubDirectories="false"/> </AssemblyResolution>`|  
  
## <a name="see-also"></a>См. также  
 [Настройка анализа покрытия кода](../test/customizing-code-coverage-analysis.md)   
 [Указание параметров тестирования для тестов Visual Studio](http://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901)
