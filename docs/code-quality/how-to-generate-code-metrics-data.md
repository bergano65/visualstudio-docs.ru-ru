---
title: Создание метрик кода из IDE или командной строки
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1abae26ed8a5e5db74f7b0d04db66d9d99930d5c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649329"
---
# <a name="how-to-generate-code-metrics-data"></a>Как: Создание данных метрик кода

Данные метрик кода можно генерировать тремя способами:

- Устанавливая [анализаторы FxCop](#fxcop-analyzers-code-metrics-rules) и включая четыре содержащихся в нем правила метрик кода (maintainability).

- Выбирая команду меню [ **«Анализ** > рассчитание кода метрик»](#calculate-code-metrics-menu-command) в Visual Studio.

- Из [командной строки](#command-line-code-metrics) для проектов «Си» и «Визуальные основы».

## <a name="fxcop-analyzers-code-metrics-rules"></a>Правила кодовых показателей анализаторов FxCop

[Пакет FxCopAnalyzers NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) включает в себя несколько правил [анализатиров](roslyn-analyzers-overview.md) метрик кода:

- [CA1501](ca1501-avoid-excessive-inheritance.md)
- [CA1502](ca1502.md)
- [CA1505](ca1505.md)
- [CA1506](ca1506.md)

Эти правила отключены по умолчанию, но вы можете включить их из [**Solution Explorer**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) или в [файле набора правил.](using-rule-sets-to-group-code-analysis-rules.md) Например, для включения правила CA1502 в качестве предупреждения файл "правила" будет содержать следующую запись:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules" Description="Rules" ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1502" Action="Warning" />
  </Rules>
</RuleSet>
```

### <a name="configuration"></a>Конфигурация

Можно настроить пороги, на которых правила кодовых метрик в пакете анализаторов FxCop.

1. Создание текстового файла. В качестве примера можно назвать *CodeMetricsConfig.txt.*

2. Добавьте желаемые пороги в текстовый файл в следующем формате:

   ```txt
   CA1502: 10
   ```

   В этом примере правило [CA1502](ca1502.md) настроено на стрельбу, когда цикломатическая сложность метода превышает 10.

3. В окне **свойств** Visual Studio или в файле проекта отметьте действие сборки файла конфигурации как [**AdditionalFiles.**](../ide/build-actions.md#build-action-values) Пример:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Рассчитайте команду меню метрик кода

Создайте метрики кода для одного или всех открытых проектов в IDE с помощью меню **Analyse** > **Calculate Code Metrics.**

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Создание результатов метрик кода для всего решения

Результаты метрик кода можно генерировать в любом из следующих способов:

- Из меню бар, выберите **Анализ** > **рассчитать код метрик** > **для решения**.

- В **Solution Explorer**, правой кнопкой мыши решения, а затем выбрать **Рассчитать код метрики**.

- В окне **результатов индекса кода** выберите кнопку **«Рассчитать код для решения».**

Результаты генерируются и отображается окно **результатов кода.** Чтобы просмотреть детали результатов, расширьте дерево в столбце **Иерархии.**

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Создание результатов метрик кода для одного или нескольких проектов

1. В **Solution Explorer**выберите один или несколько проектов.

1. Из панели меню выберите **Анализ** > **метрик** > кода**для выбранного проекта (ы)**.

Результаты генерируются и отображается окно **результатов кода.** Чтобы просмотреть детали результатов, расширьте дерево в **Иерархии.**

::: moniker range="vs-2017"

> [!NOTE]
> Команда **Calculate Code Metrics** не работает для проектов .NET Core и .NET Standard. Вычислить метрики кода для проекта .NET Core или .NET Standard можно:
>
> - Рассчитайте метрики кода из [командной строки](#command-line-code-metrics)
>
> - Обновление до [визуальной студии 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Метрики кода командной строки

Вы можете генерировать данные о метриках кода из командной строки для проектов СЗ и Visual Basic для приложений .NET Framework, .NET Core и .NET Standard. Чтобы запустить метрики кода из командной строки, установите [пакет Microsoft.CodeAnalysis.Metrics NuGet](#microsoftcodeanalysismetrics-nuget-package) или создайте исключительную [метрику Metrics.exe.](#metricsexe)

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Пакет Microsoft.CodeAnalysis.Metrics NuGet

Самый простой способ генерации данных о метриках кода из командной строки — это установка пакета [Microsoft.CodeAnalysis.Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) NuGet. После установки пакета выполнить `msbuild /t:Metrics` из каталога, который содержит файл проекта. Пример:

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

Вы можете переопределить имя файла `/p:MetricsOutputFile=<filename>`вывода, указав. Вы также можете получить [устаревшие](#previous-versions) данные `/p:LEGACY_CODE_METRICS_MODE=true`метрик кода, указав. Пример:

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

### <a name="code-metrics-output"></a>Выход метрик кода

Вывод XML занимает следующий формат:

::: moniker range=">=vs-2019"
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
          <Metric Name="SourceLines" Value="11" />
          <Metric Name="ExecutableLines" Value="1" />
        </Metrics>
        <Namespaces>
          <Namespace Name="ConsoleApp20">
            <Metrics>
              <Metric Name="MaintainabilityIndex" Value="100" />
              <Metric Name="CyclomaticComplexity" Value="1" />
              <Metric Name="ClassCoupling" Value="1" />
              <Metric Name="DepthOfInheritance" Value="1" />
              <Metric Name="SourceLines" Value="11" />
              <Metric Name="ExecutableLines" Value="1" />
            </Metrics>
            <Types>
              <NamedType Name="Program">
                <Metrics>
                  <Metric Name="MaintainabilityIndex" Value="100" />
                  <Metric Name="CyclomaticComplexity" Value="1" />
                  <Metric Name="ClassCoupling" Value="1" />
                  <Metric Name="DepthOfInheritance" Value="1" />
                  <Metric Name="SourceLines" Value="7" />
                  <Metric Name="ExecutableLines" Value="1" />
                </Metrics>
                <Members>
                  <Method Name="void Program.Main(string[] args)" File="C:\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
                    <Metrics>
                      <Metric Name="MaintainabilityIndex" Value="100" />
                      <Metric Name="CyclomaticComplexity" Value="1" />
                      <Metric Name="ClassCoupling" Value="1" />
                      <Metric Name="SourceLines" Value="4" />
                      <Metric Name="ExecutableLines" Value="1" />
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
::: moniker-end
::: moniker range="vs-2017"
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
::: moniker-end

### <a name="metricsexe"></a>Metrics.exe

Если вы не хотите устанавливать пакет NuGet, вы можете создавать и использовать *Metrics.exe,* исполняемый напрямую. Для создания *Metrics.exe* исполняемый:

1. Клонировать [dotnet / рослин-анализаторов](https://github.com/dotnet/roslyn-analyzers) репо.
2. Открытый запрос команды разработчиков для Visual Studio в качестве администратора.
3. Из корня **репо рослин-анализаторов** выполните следующую команду:`Restore.cmd`
4. Изменение каталога на *src-Tools*.
5. Выполните следующую команду для создания проекта **Metrics.csproj:**

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Исполняемое имя *Metrics.exe* генерируется в каталоге *артефактов* под корнем репо.

#### <a name="metricsexe-usage"></a>Использование Metrics.exe

Для запуска *Metrics.exe*, поставка проекта или решения и вывода XML файл в качестве аргументов. Пример:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Устаревший режим

Вы можете построить *Metrics.exe* в *устаревшем режиме.* Устаревшая версия инструмента генерирует метрические значения, которые ближе к более [старым версиям генерируемого инструмента.](#previous-versions) Кроме того, в устаревшем режиме *Metrics.exe* генерирует метрики кода для того же набора типов методов, для которых предыдущие версии инструмента генерировали метрики кода. Например, он не генерирует данные метрик кода для инициализаторов полей и свойств. Режим «Наследие» полезен для обратной совместимости или если у вас есть ворота регистрации кода на основе чисел метрик кода. Команда для создания *Metrics.exe* в устаревшем режиме:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Для получения дополнительной информации [см.](https://github.com/dotnet/roslyn-analyzers/pull/1841)

### <a name="previous-versions"></a>Предыдущие версии

::: moniker range=">=vs-2019"
Visual Studio 2015 включил командную строку кода метрик инструмент, который также назывался *Metrics.exe*. Эта предыдущая версия инструмента сделала двоичный анализ, то есть сборочный анализ. Новая версия инструмента *Metrics.exe* анализирует исходный код. Поскольку новый инструмент *Metrics.exe* основан на исходном коде, результаты метрик кода командной строки могут отличаться от результатов, генерируемых Visual Studio IDE и предыдущими *версиями Metrics.exe.* Начиная с Visual Studio 2019, Visual Studio IDE анализирует исходный код, как инструмент командной строки и результаты должны быть одинаковыми.

::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2015 включил командную строку кода метрик инструмент, который также назывался *Metrics.exe*. Эта предыдущая версия инструмента сделала двоичный анализ, то есть сборочный анализ. Вместо этого новый инструмент *Metrics.exe* анализирует исходный код. Поскольку новый инструмент *Metrics.exe* основан на исходном коде, результаты метрик кода командной строки отличаются от результатов, генерируемых Visual Studio IDE и предыдущими *версиями Metrics.exe.*
::: moniker-end

Новый инструмент метрик кода командной строки вычисляет метрики даже при наличии ошибок исходного кода, при посыле решения и проекта.

#### <a name="metric-value-differences"></a>Метрические различия в стоимости

::: moniker range=">=vs-2019"
Начиная с Visual Studio 2019 версии 16.4 и Microsoft.CodeAnalysis.Metics (2.9.5), `SourceLines` и `ExecutableLines` заменить предыдущий `LinesOfCode` показатель. Описания новых метрик [см.](../code-quality/code-metrics-values.md) Метрика `LinesOfCode` доступна в устаревшем режиме.
::: moniker-end
::: moniker range="vs-2017"
Метрика `LinesOfCode` является более точной и надежной в новом инструменте метрик кода командной строки. Он не зависит от каких-либо различий в кодегене и не изменяется при изменении набора инструментов или времени выполнения. Новый инструмент учитывает фактические строки кода, включая пустые строки и комментарии.
::: moniker-end

Другие метрики, `CyclomaticComplexity` такие как и использовать те же формулы, что и `MaintainabilityIndex` предыдущие версии *Metrics.exe*, но новый инструмент подсчитывает количество `IOperations` (логические инструкции источника) вместо промежуточных инструкций языка (IL). Цифры будут немного отличаться от тех, которые генерируются Visual Studio IDE и предыдущими *версиями Metrics.exe*.

## <a name="see-also"></a>См. также

- [Использование окна результатов кодовых метрик](../code-quality/working-with-code-metrics-data.md)
- [Значения метрик кода](../code-quality/code-metrics-values.md)
