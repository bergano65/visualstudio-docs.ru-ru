---
title: Сформировать показатели кода из командной строки или интегрированной среды разработки
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4275e92b21289c5cf1e3243b2bc782a9e0821fde
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232753"
---
# <a name="how-to-generate-code-metrics-data"></a>Практическое руководство. Создание данных для метрик кода

Данные метрик кода можно создать тремя способами:

- Установив [анализаторы FxCop](#fxcop-analyzers-code-metrics-rules) и включение правил четыре кода метрики (удобства поддержки), он содержит.

- Выбрав [ **анализ** > **Рассчитать метрики кода** ](#calculate-code-metrics-menu-command) команды меню в Visual Studio.

- Из [командной строки](#command-line-code-metrics) для C# и проекты Visual Basic.

## <a name="fxcop-analyzers-code-metrics-rules"></a>Анализаторы FxCop правила метрик кода

[Пакет FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) включает в себя несколько метрик кода [анализатор](roslyn-analyzers-overview.md) правила:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502-avoid-excessive-complexity.md)
- [CA1505](ca1505-avoid-unmaintainable-code.md)
- [CA1506](ca1506-avoid-excessive-class-coupling.md)

Эти правила отключены по умолчанию, но вы можете включить их из [ **обозревателе решений** ](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) или в [набор правил](using-rule-sets-to-group-code-analysis-rules.md) файл. Например чтобы включить правило CA1502 как предупреждение, RULESET-файл будет содержать следующую запись:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Параметр Configuration

Вы можете настроить пороговые значения, по которым правила метрик кода в анализаторы FxCop упаковать пожара.

1. Создание текстового файла. В качестве примера можно назвать его *CodeMetricsConfig.txt*.

2. Добавьте необходимые пороги текстового файла в следующем формате:

   ```txt
   CA1502: 10
   ```

   В этом примере правило [CA1502](ca1502-avoid-excessive-complexity.md) настраивается на срабатывание при метода Цикломатическая сложность превышает 10.

3. В **свойства** окно Visual Studio, или в файле проекта, пометить действие построения о файле конфигурации как [ **AdditionalFiles**](../ide/build-actions.md#build-action-values). Пример:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Рассчитать метрики кода команды меню

Создание метрики кода для один или все открытые проекты в интегрированной среде разработки с помощью **анализ** > **Рассчитать метрики кода** меню.

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Создание результатов метрики кода для всего решения

Вы можете создать Результаты метрик кода для всего решения в любом из следующих способов:

- В строке меню выберите **анализ** > **Рассчитать метрики кода** > **для решения**.

- В **обозревателе решений**, щелкните правой кнопкой мыши решение и выберите пункт **Рассчитать метрики кода**.

- В **результатов метрики кода** окно, выберите **Рассчитать метрики кода для решения** кнопки.

Результаты создаются и **результатов метрики кода** откроется диалоговое окно. Чтобы просмотреть подробные результаты, раскройте дерево на **иерархии** столбца.

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Создание результатов метрики кода для одного или нескольких проектов

1. В **обозревателе решений**, выберите один или несколько проектов.

1. В строке меню выберите **анализ** > **Рассчитать метрики кода** > **для выбранных проектов**.

Результаты создаются и **результатов метрики кода** откроется диалоговое окно. Чтобы просмотреть подробные результаты, раскройте дерево на **иерархии**.

::: moniker range="vs-2017"

> [!NOTE]
> **Рассчитать метрики кода** команда не работает для проектов .NET Core и .NET Standard. Чтобы рассчитать метрики кода для проекта .NET Core или .NET Standard, вы можете:
>
> - Рассчитать метрики кода из [командной строки](#command-line-code-metrics) вместо
>
> - Обновление до [2019 г. Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

::: moniker-end

## <a name="command-line-code-metrics"></a>Метрики кода командной строки

Вы можете создать данные метрик кода из командной строки для C# и проекты Visual Basic для приложений .NET Framework, .NET Core и .NET Standard. Для метрик кода запуска из командной строки, установить [пакет Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) или построения [Metrics.exe](#metricsexe) исполняемый самостоятельно.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Пакет Microsoft.CodeAnalysis.Metrics NuGet

Самый простой способ получения данных метрик кода из командной строки является установка [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) пакет NuGet. После установки пакета, запустите `msbuild /t:Metrics` из каталога, содержащего файл проекта. Пример:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:29:57 PM.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics\Metrics.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:ClassLibrary3.Metrics.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'ClassLibrary3.Metrics.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

Имя выходного файла можно переопределить, указав `/p:MetricsOutputFile=<filename>`. Можно также получить [прежних](#previous-versions) кода данных метрик, указав `/p:LEGACY_CODE_METRICS_MODE=true`. Пример:

```shell
C:\source\repos\ClassLibrary3\ClassLibrary3>msbuild /t:Metrics /p:LEGACY_CODE_METRICS_MODE=true /p:MetricsOutputFile="Legacy.xml"
Microsoft (R) Build Engine version 16.0.360-preview+g9781d96883 for .NET Framework
Copyright (C) Microsoft Corporation. All rights reserved.

Build started 1/22/2019 4:31:00 PM.
The "MetricsOutputFile" property is a global property, and cannot be modified.
Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" on node 1 (Metrics target(s))
.
Metrics:
  C:\source\repos\ClassLibrary3\packages\Microsoft.CodeMetrics.2.6.4-ci\build\\..\Metrics.Legacy\Metrics.Legacy.exe /project:C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj /out:Legacy.xml
  Loading ClassLibrary3.csproj...
  Computing code metrics for ClassLibrary3.csproj...
  Writing output to 'Legacy.xml'...
  Completed Successfully.
Done Building Project "C:\source\repos\ClassLibrary3\ClassLibrary3\ClassLibrary3.csproj" (Metrics target(s)).

Build succeeded.
    0 Warning(s)
    0 Error(s)
```

### <a name="code-metrics-output"></a>Выходные данные метрик кода

Созданные выходные данные XML имеет следующий формат:

```xml
<?xml version="1.0" encoding="utf-8"?>
<CodeMetricsReport Version="1.0">
  <Targets>
    <Target Name="ConsoleApp20.csproj">
      <Assembly Name="ConsoleApp20, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null">
        <Metrics>
          <Metric Name="MaintainabilityIndex" Value="100" />
          <Metric Name="CyclomaticComplexity" Value="1" />
          <Metric Name="ClassCoupling" Value="1" />
          <Metric Name="DepthOfInheritance" Value="1" />
          <Metric Name="LinesOfCode" Value="11" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="LinesOfCode" Value="11" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="LinesOfCode" Value="7" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="LinesOfCode" Value="4" />
                    </Metrics>
                  </Method>
                </Members>
              </NamedType>
            </Types>
          </Namespace>
        </Namespaces>
      </Assembly>
    </Target>
  </Targets>
</CodeMetricsReport>
```

### <a name="metricsexe"></a>Metrics.exe

Если вы не хотите установить пакет NuGet, можно создать и использовать *Metrics.exe* исполняемый файл напрямую. Для создания *Metrics.exe* исполняемого файла:

1. Клон [dotnet/анализаторов roslyn](https://github.com/dotnet/roslyn-analyzers) репозитория.
2. Откройте командную строку разработчика для Visual Studio с правами администратора.
3. Из корневого каталога **анализаторов roslyn** репозитория, выполните следующую команду: `Restore.cmd`
4. Перейдите в каталог *src\Tools*.
5. Выполните следующую команду для создания **Metrics.csproj** проекта:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Исполняемый файл с именем *Metrics.exe* создается в *artifacts\bin* каталог в корневом каталоге репозитория.

#### <a name="metricsexe-usage"></a>Использование Metrics.exe

Для запуска *Metrics.exe*, укажите проект или файл решения и выходные данные XML, как аргументы. Пример:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Устаревший режим

Вы можете создавать *Metrics.exe* в *устаревший режим*. Устаревший режим версии средство создает значения метрик, которые ближе к что [более старых версиях созданных средством](#previous-versions). Кроме того, в стандартном режиме *Metrics.exe* создает метрики кода для того же набора метод типов, предыдущие версии метрики средство для создания кода для. Например он не создает данными метрик кода для инициализаторов поля и свойства. Устаревший режим полезно для обратной совместимости, или если у вас есть код возврата шлюзы на основе метрик кода чисел. Команда для создания *Metrics.exe* в стандартном режиме:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Дополнительные сведения см. в разделе [включить формирование показатели качества кода в стандартном режиме](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>Предыдущие версии

Visual Studio 2015 содержит средство метрики командной строки кода, который также был вызван *Metrics.exe*. Предыдущей версии средства делали двоичный анализ, то есть анализ на основе сборки. Новый *Metrics.exe* средство анализирует исходный код, вместо этого. Так как новый *Metrics.exe* средство — метрики кода на уровне кода, командной строки источника, результаты будут другими, которые создаются с помощью Visual Studio IDE и предыдущими версиями *Metrics.exe*.

Новое средство командной строки кода метрики вычисляет метрики даже при наличии исходного кода ошибки, до тех пор, пока решение и проект может загружаться.

#### <a name="metric-value-differences"></a>Различия значение метрики

`LinesOfCode` Метрика — это более точным и надежным в новые метрики средство командной строки кода. Он не зависит от какие-либо различия codegen и не меняется при изменении набора инструментов или среды выполнения. Новое средство подсчитывать фактические строки кода, включая пустые строки и комментарии.

Другие метрики, такие как `CyclomaticComplexity` и `MaintainabilityIndex` использование тех же формул в предыдущих версиях *Metrics.exe*, но новое средство подсчитывает количество `IOperations` (логического исходного инструкций) вместо промежуточного инструкции языка (IL). Номера будет немного отличаться, которые создаются с помощью Visual Studio IDE и предыдущими версиями *Metrics.exe*.

## <a name="see-also"></a>См. также

- [В окне результатов метрики кода](../code-quality/working-with-code-metrics-data.md)
- [Значения метрик кода](../code-quality/code-metrics-values.md)
