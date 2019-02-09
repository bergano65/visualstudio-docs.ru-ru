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
ms.openlocfilehash: 2d8aa9a1f369b228b7e1c68a12381bf52d692173
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909210"
---
# <a name="how-to-generate-code-metrics-data"></a>Как выполнить  Создание данных для метрик кода

Вы можете создать Результаты метрик кода для одного или нескольких проектов или всего решения. Метрики кода доступен в среде разработки Visual Studio (IDE), а также для C# и проекты Visual Basic, в командной строке.

Кроме того, можно установить [пакет NuGet](https://dotnet.myget.org/feed/roslyn-analyzers/package/nuget/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.2-beta2-63202-01) , включает в себя четыре метрики кода [анализатор](roslyn-analyzers-overview.md) правила: CA1501, CA1502, CA1505 и CA1506. Эти правила отключены по умолчанию, но вы можете включить их из **обозревателе решений** или в [набор правил](using-rule-sets-to-group-code-analysis-rules.md) файл.

## <a name="visual-studio-ide-code-metrics"></a>Метрики кода для Visual Studio IDE

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

Предыдущие версии Visual Studio, включая Visual Studio 2015 включено средство метрики командной строки кода, который также был вызван *Metrics.exe*. Предыдущей версии средства делали двоичный анализ, то есть анализ на основе сборки. Новое средство анализирует исходный код вместо этого. Так как метрики средства командной строки кода в новый источник, на основе кода, результаты будут другими к обеспечиваемому предыдущих версий *Metrics.exe* и интегрированной среды разработки Visual Studio 2017.

Новое средство командной строки кода метрики вычисляет метрики даже при наличии исходного кода ошибки, до тех пор, пока решение и проект может загружаться.

#### <a name="metric-value-differences"></a>Различия значение метрики

`LinesOfCode` Метрика — это более точным и надежным в новые метрики средство командной строки кода. Он не зависит от какие-либо различия codegen и не меняется при изменении набора инструментов или среды выполнения. Новое средство подсчитывать фактические строки кода, включая пустые строки и комментарии.

Другие метрики, такие как `CyclomaticComplexity` и `MaintainabilityIndex` использование тех же формул в предыдущих версиях *Metrics.exe*, но новое средство подсчитывает количество `IOperations` (логического исходного инструкций) вместо промежуточного инструкции языка (IL). Номера будут немного отличаться от предыдущих версий *Metrics.exe* и из результатов метрики кода интегрированной среды разработки для Visual Studio 2017.

## <a name="see-also"></a>См. также

- [В окне результатов метрики кода](../code-quality/working-with-code-metrics-data.md)
- [Значения метрик кода](../code-quality/code-metrics-values.md)
