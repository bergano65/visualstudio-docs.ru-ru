---
title: Сформировать показатели кода из командной строки или интегрированной среды разработки
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f34f686b91d6a140e975c13eec72e8703a1b47ef
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945259"
---
# <a name="how-to-generate-code-metrics-data"></a>Как выполнить Создание данных для метрик кода

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

Вы можете создать данные метрик кода из командной строки для C# и проекты Visual Basic для приложений .NET Framework, .NET Core и .NET Standard. Программы командной строки кода метрики называется *Metrics.exe*.

Для получения *Metrics.exe* исполняемый файл, вы должны [создавать их самостоятельно](#generate-the-executable). В ближайшем будущем [опубликованная версия *Metrics.exe* будут доступны](https://github.com/dotnet/roslyn-analyzers/issues/1756) , вам не нужно создавать самостоятельно.

### <a name="generate-the-executable"></a>Создания исполняемого файла

Для создания исполняемого файла *Metrics.exe*, выполните следующие действия:

1. Клон [dotnet/анализаторов roslyn](https://github.com/dotnet/roslyn-analyzers) репозитория.
2. Откройте командную строку разработчика для Visual Studio с правами администратора.
3. Из корневого каталога **анализаторов roslyn** репозитория, выполните следующую команду: `Restore.cmd`
4. Перейдите в каталог *src\Tools*.
5. Выполните следующую команду для создания **Metrics.csproj** проекта:

   ```shell
   msbuild /m /v:m /p:Configuration=Release Metrics.csproj
   ```

   Исполняемый файл с именем *Metrics.exe* создается в *artifacts\bin* каталог в корневом каталоге репозитория.

   > [!TIP]
   > Для создания *Metrics.exe* в [устаревший режим](#legacy-mode), выполните следующую команду:
   >
   > ```shell
   > msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
   > ```

### <a name="usage"></a>Использование

Для запуска *Metrics.exe*, укажите проект или файл решения и выходные данные XML, как аргументы. Пример:

```shell
C:\>Metrics.exe /project:ConsoleApp20.csproj /out:report.xml
Loading ConsoleApp20.csproj...
Computing code metrics for ConsoleApp20.csproj...
Writing output to 'report.xml'...
Completed Successfully.
```

### <a name="output"></a>Вывод

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
                  <Method Name="void Program.Main(string[] args)" File="C:\Users\mavasani\source\repos\ConsoleApp20\ConsoleApp20\Program.cs" Line="7">
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

### <a name="tool-differences"></a>Средство различия

Предыдущие версии Visual Studio, включая Visual Studio 2015, включены метрики средство командной строки кода *Metrics.exe*. Предыдущей версии средства делали двоичный анализ, то есть анализ на основе сборки. Новое средство анализирует исходный код вместо этого. Так как новый *Metrics.exe* основана на исходный код, результаты будут другими к обеспечиваемому предыдущих версий *Metrics.exe* и интегрированной среды разработки Visual Studio 2017.

Новый *Metrics.exe* средство может вычислить метрики даже при наличии ошибок кода источника, до тех пор, пока решение и проект может загружаться.

#### <a name="metric-value-differences"></a>Различия значение метрики

`LinesOfCode` Метрика — это более точным и надежным в новом *Metrics.exe*. Он не зависит от какие-либо различия codegen и не меняется при изменении набора инструментов или среды выполнения. Новый *Metrics.exe* подсчитывать фактические строки кода, включая пустые строки и комментарии.

Другие метрики, такие как `CyclomaticComplexity` и `MaintainabilityIndex` использование тех же формул в предыдущих версиях *Metrics.exe*, однако новый *Metrics.exe* подсчитывает количество `IOperations` (логический источника инструкции) вместо инструкций промежуточного языка (IL). Номера будут немного отличаться от предыдущих версий *Metrics.exe* и из результатов метрики кода интегрированной среды разработки для Visual Studio 2017.

### <a name="legacy-mode"></a>Устаревший режим

Вы также можете создавать *Metrics.exe* в *устаревший режим*. Устаревший режим версии средство создает значения метрик, которые ближе к какой более старых версиях созданных средством. Кроме того, в стандартном режиме *Metrics.exe* создает метрики кода для того же набора метод типов, предыдущие версии метрики средство для создания кода для. Например он не создает данными метрик кода для инициализаторов поля и свойства. Устаревший режим полезно для обратной совместимости, или если у вас есть код возврата шлюзы на основе метрик кода чисел. Команда для создания *Metrics.exe* в стандартном режиме:

```shell
msbuild /m /v:m /t:rebuild /p:LEGACY_CODE_METRICS_MODE=true Metrics.csproj
```

Дополнительные сведения см. в разделе [включить формирование показатели качества кода в стандартном режиме](https://github.com/dotnet/roslyn-analyzers/pull/1841).

## <a name="see-also"></a>См. также

- [В окне результатов метрики кода](../code-quality/working-with-code-metrics-data.md)
- [Значения метрик кода](../code-quality/code-metrics-values.md)
