---
title: Миграция с FxCop на исходный анализ (FxCop Analyzer)
ms.custom: SEO-VS-2020
description: Узнайте, как анализировать код в первый раз или как выполнить миграцию из двоичного анализа (FxCop) к новому способу анализа управляемого кода с помощью анализа источника (FxCop Analyzer).
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ce3c8feb3d3bbd458c14ee702d6e8a1668078f3
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658481"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Переход от традиционного анализа (FxCop) к исходному анализу (FxCop Analyzer)

Анализ исходного кода с помощью анализаторов .NET Compiler Platform ("Roslyn") заменяет [устаревший анализ](../code-quality/code-analysis-for-managed-code-overview.md) управляемому коду. Для новых шаблонов проектов, таких как проекты .NET Core и .NET Standard, устаревший анализ недоступен.

Многие правила традиционного анализа (FxCop) уже были переписаны для средств FxCop Analyzer, набора анализаторов кода Roslyn. [Анализаторы FxCop устанавливаются в виде пакета NuGet](install-fxcop-analyzers.md#nuget-package) , на который ссылается проект или решение. Анализаторы FxCop осуществляют анализ на основе исходного кода во время выполнения компилятора. Результаты работы анализатора выводятся вместе с результатами выполнения компилятора.

Дополнительные сведения о различиях между анализом прежних версий и анализом исходного кода см. в следующих статьях:

- [Сравнение анализа исходного кода и устаревшей функции анализа](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers)

- [Вопросы и ответы об анализаторах FxCop](../code-quality/fxcop-analyzers-faq.md)

Чтобы выполнить миграцию в исходный анализ, [установите анализаторы FxCop](../code-quality/install-fxcop-analyzers.md). Как и в случае нарушений правил устаревшей функции анализа, нарушения анализа исходного кода отображаются в Visual Studio в окне списка ошибок. Кроме того, нарушения анализа исходного кода выделяются в редакторе кода с помощью *волнистых линий* под соответствующим кодом. Цвет волнистой линии зависит [параметра серьезности](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) правила. Сведения о правилах, переданных в новые анализаторы FxCop, см. в статье [правила переноса и неперенесенных](../code-quality/fxcop-rule-port-status.md)правил.

Дополнительные сведения о настройке анализаторов FxCop:

- Сведения о настройке анализаторов FxCop см. в статье [Настройка средств FxCop Analyzer](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- Чтобы узнать о настройке анализаторов с помощью стандартных правил с EditorConfig или файла набора правил, см. раздел [Включение категории правил](/dotnet/fundamentals/code-analysis/code-quality-rule-options).