---
title: Создание метрик кода из интегрированной среды разработки или командной строки
ms.date: 11/02/2018
description: Узнайте, как создавать данные метрик кода в Visual Studio. Узнайте, как использовать обозреватель решений, файл набора правил, командную строку или команду меню.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code metrics data
- code metrics results
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa0512e5d29cb1b5c5a39715e34667803b752795
ms.sourcegitcommit: 04954be0c4373f82f79181e1a5e7812be4d3e1f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496266"
---
# <a name="how-to-generate-code-metrics-data"></a>Как создавать данные метрик кода

Данные метрик кода можно создавать тремя способами:

- Включив [анализаторы качества кода .NET](#net-code-quality-analyzers-code-metrics-rules) и включив в него четыре метрики кода (сопровождаемость).

- Выбрав команду меню [ **анализ**  >  **метрики кода**](#calculate-code-metrics-menu-command) в Visual Studio.

- Из [командной строки](#command-line-code-metrics) для проектов C# и Visual Basic.

## <a name="net-code-quality-analyzers-code-metrics-rules"></a>Правила метрик кода для анализаторов качества кода .NET

Анализаторы качества кода .NET включают несколько правил [анализатора](roslyn-analyzers-overview.md) кода метрик:

- [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501)
- [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)
- [CA1505](/dotnet/fundamentals/code-analysis/quality-rules/ca1505)
- [CA1506](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

Эти правила по умолчанию отключены, но их можно включить в [**Обозреватель решений**](use-roslyn-analyzers.md#set-rule-severity-from-solution-explorer) или в файле [EditorConfig](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file) . Например, чтобы включить правило CA1502 в виде предупреждения, файл EditorConfig будет содержать следующую запись:

```cs
dotnet_diagnostic.CA1502.severity = warning
```

### <a name="configuration"></a>Конфигурация

Вы можете настроить пороговые значения, при которых будут срабатывать правила метрики кода.

1. Создание текстового файла. Например, можно присвоить имя *CodeMetricsConfig.txt*.

2. Добавьте необходимые пороговые значения в текстовый файл в следующем формате:

   ```txt
   CA1502: 10
   ```

   В этом примере правило [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502) настраивается на срабатывание, когда сложность сложностью организации циклов метода больше 10.

3. В окне **Свойства** Visual Studio или в файле проекта пометьте действие сборки файла конфигурации как [**аддитионалфилес**](../ide/build-actions.md#build-action-values). Пример:

   ```xml
   <ItemGroup>
     <AdditionalFiles Include="CodeMetricsConfig.txt" />
   </ItemGroup>
   ```

## <a name="calculate-code-metrics-menu-command"></a>Команда меню «вычислить метрики кода»

Создайте метрики кода для одного или всех открытых проектов в интегрированной среде разработки с помощью меню **анализ**  >  **метрик кода** .

### <a name="generate-code-metrics-results-for-an-entire-solution"></a>Создание результатов метрик кода для всего решения

Вы можете создавать Результаты метрик кода для всего решения одним из следующих способов:

- В строке меню выберите **анализ**  >  **рассчитать метрики кода**  >  **для решения**.

- В **Обозреватель решений** щелкните правой кнопкой мыши решение и выберите пункт **рассчитать метрики кода**.

- В окне **Результаты метрик кода** выберите кнопку **вычислить метрики кода для решения** .

Результаты будут сформированы, и откроется окно **результаты метрики кода** . Чтобы просмотреть подробные сведения о результатах, разверните дерево в столбце **Иерархия** .

### <a name="generate-code-metrics-results-for-one-or-more-projects"></a>Создание результатов метрик кода для одного или нескольких проектов

1. В **Обозреватель решений** выберите один или несколько проектов.

1. В строке меню выберите **анализ**  >  **рассчитать метрики кода**  >  **для выбранных проектов**.

Результаты будут сформированы, и откроется окно **результаты метрики кода** . Чтобы просмотреть подробные сведения о результатах, разверните дерево в **иерархии**.

::: moniker range="vs-2017"

> [!NOTE]
> Команда " **вычислить метрики кода** " не работает для проектов .NET Core и .NET Standard. Чтобы рассчитать метрики кода для проекта .NET Core или .NET Standard, можно:
>
> - Вместо этого вычислить метрики кода из [командной строки](#command-line-code-metrics)
>
> - Обновление до [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

## <a name="command-line-code-metrics"></a>Метрики кода командной строки

Вы можете создавать данные метрик кода из командной строки для проектов C# и Visual Basic для платформа .NET Framework, .NET Core и .NET Standard приложений. Чтобы запустить метрики кода из командной строки, установите [пакет NuGet Microsoft. CodeAnalysis. Metrics](#microsoftcodeanalysismetrics-nuget-package) или [Metrics.exe](#metricsexe) Создайте исполняемый файл самостоятельно.

### <a name="microsoftcodeanalysismetrics-nuget-package"></a>Пакет NuGet Microsoft. CodeAnalysis. Metrics

Самый простой способ создать данные метрик кода из командной строки — установить пакет NuGet [Microsoft. CodeAnalysis. Metrics](https://www.nuget.org/packages/Microsoft.CodeAnalysis.Metrics/) . После установки пакета запустите `msbuild /t:Metrics` из каталога, содержащего файл проекта. Пример:

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

Можно переопределить имя выходного файла, указав `/p:MetricsOutputFile=<filename>` . Вы также можете получить данные метрик кода в [стиле прежних версий](#previous-versions) , указав `/p:LEGACY_CODE_METRICS_MODE=true` . Пример:

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

Созданный выход XML имеет следующий формат:

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

Если вы не хотите устанавливать пакет NuGet, вы можете создать и использовать *Metrics.exe* исполняемый файл напрямую. Чтобы создать *Metrics.exe* исполняемый файл:

1. Клонировать репозиторий [DotNet/Roslyn-Analyzers](https://github.com/dotnet/roslyn-analyzers) .
2. Откройте Командная строка разработчика для Visual Studio с правами администратора.
3. В корне репозитория **Roslyn-Analyzers** выполните следующую команду: `Restore.cmd`
4. Измените каталог на *срк\тулс\метрикс*.
5. Выполните следующую команду, чтобы выполнить сборку проекта **метрик. csproj** :

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Исполняемый файл с именем *Metrics.exe* создается в каталоге *артифактс\бин* в корне репозитория.

#### <a name="metricsexe-usage"></a>Использование Metrics.exe

Чтобы запустить *Metrics.exe*, укажите проект или решение и выходной XML-файл в качестве аргументов. Пример:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

#### <a name="legacy-mode"></a>Устаревший режим

Можно выбрать сборку *Metrics.exe* в *устаревшем режиме*. Версия средства в устаревшем режиме создает значения метрик, которые ближе к [более старым версиям созданного средства](#previous-versions). Кроме того, в устаревшем режиме *Metrics.exe* создает метрики кода для того же набора типов методов, для которого в предыдущих версиях средства сформированы метрики кода. Например, он не создает данные метрик кода для инициализаторов полей и свойств. Устаревший режим удобен для обеспечения обратной совместимости или при наличии шлюзов возврата кода на основе номеров метрик кода. Команда для сборки *Metrics.exe* в устаревшем режиме:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Дополнительные сведения см. [в разделе Включение создания метрик кода в устаревшем режиме](https://github.com/dotnet/roslyn-analyzers/pull/1841).

### <a name="previous-versions"></a>предыдущих версий

::: moniker range=">=vs-2019"
В Visual Studio 2015 имеется средство метрик кода командной строки, которое также называлось *Metrics.exe*. Предыдущая версия средства выполняла двоичный анализ, то есть анализ на основе сборок. Более новая версия средства *Metrics.exe* анализирует исходный код. Поскольку более новая *Metrics.exe* средство является исходным кодом, результаты метрик кода командной строки могут отличаться от результатов, создаваемых интегрированной средой разработки Visual Studio и предыдущими версиями *Metrics.exe*. Начиная с Visual Studio 2019, интегрированная среда разработки Visual Studio анализирует исходный код, подобный средству командной строки, и результаты должны быть одинаковыми.

::: moniker-end
::: moniker range="vs-2017"
В Visual Studio 2015 имеется средство метрик кода командной строки, которое также называлось *Metrics.exe*. Предыдущая версия средства выполняла двоичный анализ, то есть анализ на основе сборок. Новое средство *Metrics.exe* анализирует исходный код. Поскольку новый инструмент *Metrics.exe* основан на исходном коде, результаты метрик кода командной строки отличаются от результатов, создаваемых интегрированной средой разработки Visual Studio и предыдущими версиями *Metrics.exe*.
::: moniker-end

Новое средство метрик кода командной строки выдает метрики даже при наличии ошибок исходного кода, пока решение и проект могут быть загружены.

#### <a name="metric-value-differences"></a>Различия в значениях метрик

::: moniker range=">=vs-2019"
Начиная с Visual Studio 2019 версии 16,4 и Microsoft. CodeAnalysis. метрики (2.9.5), `SourceLines` `ExecutableLines` замените предыдущую `LinesOfCode` метрику. Описание новых метрик см. в разделе [значения метрик кода](../code-quality/code-metrics-values.md). `LinesOfCode`Метрика доступна в устаревшем режиме.
::: moniker-end
::: moniker range="vs-2017"
Эта `LinesOfCode` Метрика более точная и надежная в новом инструменте для метрик кода командной строки. Он не зависит от CodeGen различий и не изменяется при изменении набора инструментов или среды выполнения. Новое средство подсчитывает фактические строки кода, включая пустые строки и комментарии.
::: moniker-end

Другие метрики, такие как `CyclomaticComplexity` и, `MaintainabilityIndex` используют те же формулы, что и предыдущие версии *Metrics.exe*, но новое средство подсчитывает количество `IOperations` (инструкции логического источника) вместо инструкций промежуточного языка (IL). Номера будут немного отличаться от тех, которые создаются в интегрированной среде разработки Visual Studio и предыдущих версиях *Metrics.exe*.

## <a name="see-also"></a>См. также раздел

- [Использование окна "Результаты метрик кода"](../code-quality/working-with-code-metrics-data.md)
- [Значения метрик кода](../code-quality/code-metrics-values.md)