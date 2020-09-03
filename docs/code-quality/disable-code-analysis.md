---
title: Отключить анализ кода
ms.date: 10/03/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2cac7ad0502d82309aa664b8e8fe6bdd0301815
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800702"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Отключение анализа исходного кода для управляемого кода

::: moniker range=">=vs-2019"

Эта страница поможет отключить анализ кода в Visual Studio. Существуют ограничения на то, что можно отключить, а процедура отключения анализа кода различается в зависимости от нескольких факторов.

- Тип проекта (.NET Core, Standard и .NET Framework)

  Проекты .NET Core и .NET Standard имеют параметры на странице свойств анализа кода, которые позволяют отключить анализ кода из анализаторов, установленных в качестве пакета NuGet. Дополнительные сведения см. в разделе [проекты .NET Core и .NET Standard](#net-core-and-net-standard-projects). Чтобы отключить анализ исходного кода для проектов .NET Framework, см. раздел [.NET Framework проекты](#net-framework-projects).

- Анализ исходного кода и анализ прежних версий

  Этот раздел относится к анализу исходного кода, а не к устаревшему (двоичному) анализу. Сведения об отключении анализа прежних версий см. [в разделе как включить и отключить анализ кода прежних версий](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="net-core-and-net-standard-projects"></a>Проекты .NET Core и .NET Standard

Начиная с Visual Studio 2019 версии 16,3, на странице свойств "анализ кода" доступны два флажка, которые позволяют управлять запуском анализаторов во время сборки и во время разработки. Эти параметры относятся к конкретному проекту.

![Включение или отключение анализа активного кода или сборки в Visual Studio](media/run-on-build-run-live-analysis.png)

Чтобы открыть эту страницу, щелкните правой кнопкой мыши узел проекта в **Обозреватель решений** и выберите пункт **свойства**. Выберите вкладку **анализ кода** .

- Чтобы отключить анализ исходного кода во время сборки, снимите флажок **выполнить при сборке** .
- Чтобы отключить анализ исходного кода, снимите флажок **выполнить при динамическом анализе** .

> [!NOTE]
> Начиная с Visual Studio 2019 версии 16,5, если вы предпочитаете рабочий процесс анализа кода по запросу, можно отключить выполнение анализатора во время динамического анализа и (или) сборку и вручную запустить анализ кода в проекте или решении по запросу. Дополнительные сведения о выполнении анализа кода вручную см. [в разделе инструкции. Запуск анализа кода вручную для управляемого кода](how-to-run-code-analysis-manually-for-managed-code.md).

## <a name="net-framework-projects"></a>Проекты .NET Framework

Чтобы отключить анализ исходного кода для анализаторов, добавьте в [файл проекта](../ide/solutions-and-projects-in-visual-studio.md#project-file)одно или несколько из следующих свойств MSBuild.

| Свойство MSBuild | Описание | По умолчанию |
| - | - | - |
| `RunAnalyzersDuringBuild` | Определяет, выполняются ли анализаторы во время сборки. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Определяет, будут ли анализаторы анализировать код в реальном времени во время разработки. | `true` |
| `RunAnalyzers` | Отключает анализаторы как на этапе сборки, так и во время разработки. Это свойство имеет приоритет над `RunAnalyzersDuringBuild` и `RunAnalyzersDuringLiveAnalysis` . | `true` |

Примеры:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Анализ источника

Вы не можете отключить [анализ исходного кода](roslyn-analyzers-overview.md) в Visual Studio 2017. Если вы хотите удалить ошибки анализатора из **Список ошибок**, можно отключить все текущие нарушения, выбрав **анализировать**  >  **выполнение анализа кода и подавлять активные проблемы** в строке меню. Дополнительные сведения см. в разделе [подавлять нарушения](use-roslyn-analyzers.md#suppress-violations).

Начиная с Visual Studio 2019 версии 16,3, можно отключить анализ исходного кода или выполнить его по требованию. Рассмотрите возможность обновления до Visual Studio 2019.

## <a name="legacy-analysis"></a>Анализ прежних версий

На странице свойств **анализа кода** можно отключить устаревший анализ времени сборки. Дополнительные сведения см. [в разделе инструкции. Включение и отключение анализа кода прежних версий](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>См. также раздел

- [Подавлять нарушения](use-roslyn-analyzers.md#suppress-violations)
- [Как включить и отключить анализ кода прежних версий](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
