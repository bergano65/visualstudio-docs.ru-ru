---
title: Выключить анализ кода
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431401"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>Как отключить анализ исходного кода для управляемого кода

::: moniker range=">=vs-2019"

Эта страница поможет отключить анализ кода в Visual Studio. Существуют ограничения на то, что можно отключить, и процедура выключения анализа кода отличается в зависимости от нескольких факторов:

- Тип проекта (.NET Core/Standard/.NET Framework)

  В проектах .NET Core и .NET Standard есть опции на странице свойств анализа кода, которые позволяют отключить анализ кода от анализаторов, установленных в виде пакета NuGet. Для получения дополнительной информации [см.](#net-core-and-net-standard-projects) Чтобы отключить анализ исходного кода для проектов .NET Framework, [см.](#net-framework-projects)

- Анализ источников и анализ наследия

  Эта тема относится к анализу исходного кода, а не к устаревшему (двоичному) анализу. Для получения информации об отключении устаревшего анализа [см.](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)

## <a name="net-core-and-net-standard-projects"></a>Проекты .NET Core и .NET Standard

Начиная с версии Visual Studio 2019 2019, на странице свойств анализа кода доступны два флажка, которые позволяют контролировать, работают ли анализаторы во время сборки и во время проектирования. Эти параметры специфичны для проекта.

![Включить или отключить анализ кода в реальном времени или при сборке в Visual Studio](media/run-on-build-run-live-analysis.png)

Чтобы открыть эту страницу, нажмите правой кнопкой мыши на узло проекта в **Solution Explorer** и выберите **Свойства.** Выберите вкладку **«Анализ кода».**

- Чтобы отключить анализ исходного кода во время сборки, отоверьте опцию **Run на сборке.**
- Чтобы отключить анализ живого источника, отоверьте запуск на опции **анализа в реальном времени.**

> [!NOTE]
> Начиная с версии Visual Studio 2019 2019, если вы предпочитаете рабочий процесс выполнения анализа анализа кода по требованию, вы можете отключить выполнение анализатора во время живого анализа и/или построить и вручную вызвать анализ кода один раз на проекте или решение по требованию. Для получения информации о запуске анализа кода вручную [см.](how-to-run-code-analysis-manually-for-managed-code.md)  

## <a name="net-framework-projects"></a>Рамочные проекты .NET

Чтобы отключить анализ исходного кода для анализаторов, добавьте один или несколько следующих свойств MSBuild в [файл проекта.](../ide/solutions-and-projects-in-visual-studio.md#project-file)

| Свойство MSBuild | Описание | По умолчанию |
| - | - | - |
| `RunAnalyzersDuringBuild` | Контролирует, работают ли анализаторы во время сборки. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | Контролирует, анализируют ли анализаторы кода в реальном времени проектирования. | `true` |
| `RunAnalyzers` | Отстраняет анализаторы как во время сборки, так и во время проектирования. Это свойство имеет `RunAnalyzersDuringBuild` приоритет `RunAnalyzersDuringLiveAnalysis`над и . | `true` |

Примеры:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>Анализ источника

Вы не можете отключить [анализ исхода](roslyn-analyzers-overview.md) в Visual Studio 2017. Если вы хотите убрать ошибки анализатора из списка ошибок, вы можете подавить все текущие нарушения, выбрав **анализ** > **кода Analyze Run и подавить активные проблемы** в панели меню. Для получения дополнительной информации [см.](use-roslyn-analyzers.md#suppress-violations)

Начиная с версии Visual Studio 2019 16.3, можно отключить анализ исходного кода или выполнить его по требованию. Рассмотрим обновление до Visual Studio 2019.

## <a name="legacy-analysis"></a>Анализ прежних версий

Можно отключить устаревший анализ времени сборки на странице свойств **анализа кода.** Для получения дополнительной информации [см. Как: Включить и отключить анализ устаревшего кода](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

::: moniker-end

## <a name="see-also"></a>См. также раздел

- [Подавление нарушений](use-roslyn-analyzers.md#suppress-violations)
- [Как: Включить и отключить анализ устаревшего кода](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
