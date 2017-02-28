---
title: "Новые возможности средств профилирования | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 1dae0fddd8f3608089b67f571e152ed5a0f56c61
ms.openlocfilehash: 888c5c996df6558fc4c409704ad003f9c25a733b
ms.lasthandoff: 02/22/2017

---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Новые возможности средств профилирования в [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
Средства диагностики включают новые визуализации, которые помогают находить в приложении проблемы, требующие устранения. Средства диагностики теперь включают поддержку приложений ASP.NET.

Дополнительные сведения см. в [заметках о выпуске [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](https://www.visualstudio.com/ru-ru/news/releasenotes/vs2017-relnotes#debuggingdiag).

В средства добавлена вкладка **Сводка**, которые позволяет сосредоточиться на ключевых областях для анализа производительности. Эта вкладка показывает, сколько событий произошло, и позволяет делать моментальные снимки кучи, а также быстро включать сбор данных по загрузке ЦП. В этом представлении приводятся все события [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) и [анализа пользовательского интерфейса](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis). Кроме того, в Visual Studio Enterprise в этом представлении также приводятся события IntelliTrace.

![Вкладка "Сводка" средств диагностики](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

В средстве анализа загрузки ЦП имеются [новые визуализации](../profiling/Beginners-Guide-to-Performance-Profiling.md), помогающий выявлять функции, которые являются наиболее вероятной причиной проблем с производительностью. Новое представление **Вызывающий/вызываемый** позволяет отслеживать затраты на вызовы функций, выполняемые из выбранной функции и к ней.

![Средства диагностики, представление "Вызывающий/вызываемый"](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>См. также  
 [Средства профилирования](../profiling/profiling-tools.md)
