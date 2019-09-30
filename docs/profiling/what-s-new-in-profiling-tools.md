---
title: Новые возможности профилирования в Visual Studio 2017 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 0512c6e95f0a26184593f7af5ba08c31c33a3299
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128340"
---
# <a name="whats-new-in-profiling-tools-in-includevs_dev15miscincludesvs_dev15_mdmd"></a>Новые возможности средств профилирования в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Средства диагностики включают новые визуализации, которые помогают находить в приложении проблемы, требующие устранения. Средства диагностики теперь включают поддержку приложений ASP.NET.

Дополнительные сведения см. в статье [Заметки о выпуске для [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](/visualstudio/releasenotes/vs2017-relnotes).

В средства добавлена вкладка **Сводка**, которые позволяет сосредоточиться на ключевых областях для анализа производительности. Эта вкладка показывает, сколько событий произошло, и позволяет делать моментальные снимки кучи, а также быстро включать сбор данных по загрузке ЦП. В этом представлении приводятся все события [Application Insights](/azure/azure-monitor/app/visual-studio) и [анализа пользовательского интерфейса](/visualstudio/releasenotes/vs2017-relnotes). Кроме того, в Visual Studio Enterprise в этом представлении также приводятся события IntelliTrace.

![Вкладка "Сводка" средств диагностики](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

В средстве анализа загрузки ЦП имеются [новые визуализации](../profiling/Beginners-Guide-to-Performance-Profiling.md), помогающий выявлять функции, которые являются наиболее вероятной причиной проблем с производительностью. Новое представление **Вызывающий/вызываемый** позволяет отслеживать затраты на вызовы функций, выполняемые из выбранной функции и к ней.

![Средства диагностики, представление "Вызывающий/вызываемый"](../profiling/media/diag-tools-caller-callee-2.png "DiagToolsCallerCallee")

## <a name="see-also"></a>См. также

- [Профилирование в Visual Studio](../profiling/index.yml)
- [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md)