---
title: "Представление \"Вызывающий/вызываемый\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0792f59f02c5b75247d5066b132cf1072d37c76a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="callercallee-view"></a>Представление «Вызывающий/вызываемый»
В представлении "Вызывающий/вызываемый" отображаются данные профилирования для выбранной функции и ее родительских и дочерних функций. Представление "Вызывающий/вызываемый" содержит три таблицы.  
  
 **Текущая функция** отображается в средней таблице и показывает данные профилирования для выбранной функции. Значения включают все вызовы функции, собранные в ходе сеанса профилирования.  
  
 **Функции, вызывавшие текущую функцию**, отображаются в верхней таблице, где показано количество значений выбранной (текущей) функции, которые были созданы вызовами из вызывающей (родительской) функции.  
  
 **Функции, которые были вызваны текущей функцией**, отображаются в нижней таблице, в которой указываются данные профилирования для вызываемых (дочерних) функций выбранной функции, когда дочерняя функция вызывалась текущей функцией.  
  
 Столбцы, которые доступны в представлении "Вызывающий/вызываемый" зависят от метода профилирования (выборка или инструментирование), с помощью которого выполнялся сбор данных, от того, были ли собраны данные памяти .NET в ходе сеанса профилирования.  
  
 Можно выбрать другую функцию, которая будет текущей. Для этого в средней части представления отчета дважды щелкните одну из функций, указанных в двух других частях представления. Представление отчета обновится автоматически в соответствии с внесенными изменениями.  
  
 Щелкнув имя столбца, можно отсортировать данные. Представление "Вызывающий/вызываемый" можно добавить дополнительные столбцы. Дополнительные сведения см. в статье [How to: Customize Report View Columns](../profiling/how-to-customize-report-view-columns.md) (Практическое руководство. Настройка столбцов представлений отчета).  
  
## <a name="see-also"></a>См. также  
 [Caller / Callee View - Sampling Data](../profiling/caller-callee-view-sampling-data.md)  (Представление "Вызывающий/вызываемый" — данные выборки)  
 [Caller/Callee View - Instrumentation Data](../profiling/caller-callee-view-instrumentation-data.md)  (Представление "Вызывающий/вызываемый" — данные инструментирования)  
 [Caller/Callee View - NET Memory Instrumentation Data](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  (Представление "Вызывающий/вызываемый" — данные инструментирования памяти .NET)  
 [Caller/Callee View - .NET Memory Sampling Data](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  (Представление "Вызывающий/вызываемый" — данные выборки памяти .NET)  
 [Caller / Callee View -  Contention Data](../profiling/caller-callee-view-contention-data.md) (Представление "Вызывающий/вызываемый" — данные о конфликтах)