---
title: "Представление \"Вызывающий/вызываемый\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
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
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 93a427234dc14174dd690a0a6f04c04e00080afd
ms.contentlocale: ru-ru
ms.lasthandoff: 07/14/2017

---
# Представление «Вызывающий/вызываемый»
<a id="callercallee-view" class="xliff"></a>
В представлении "Вызывающий/вызываемый" отображаются данные профилирования для выбранной функции и ее родительских и дочерних функций. Представление "Вызывающий/вызываемый" содержит три таблицы.  
  
 **Текущая функция** отображается в средней таблице и показывает данные профилирования для выбранной функции. Значения включают все вызовы функции, собранные в ходе сеанса профилирования.  
  
 **Функции, вызывавшие текущую функцию**, отображаются в верхней таблице, где показано количество значений выбранной (текущей) функции, которые были созданы вызовами из вызывающей (родительской) функции.  
  
 **Функции, которые были вызваны текущей функцией**, отображаются в нижней таблице, в которой указываются данные профилирования для вызываемых (дочерних) функций выбранной функции, когда дочерняя функция вызывалась текущей функцией.  
  
 Столбцы, которые доступны в представлении "Вызывающий/вызываемый" зависят от метода профилирования (выборка или инструментирование), с помощью которого выполнялся сбор данных, от того, были ли собраны данные памяти .NET в ходе сеанса профилирования.  
  
 Можно выбрать другую функцию, которая будет текущей. Для этого в средней части представления отчета дважды щелкните одну из функций, указанных в двух других частях представления. Представление отчета обновится автоматически в соответствии с внесенными изменениями.  
  
 Щелкнув имя столбца, можно отсортировать данные. Представление "Вызывающий/вызываемый" можно добавить дополнительные столбцы. Дополнительные сведения см. в статье [How to: Customize Report View Columns](../profiling/how-to-customize-report-view-columns.md) (Практическое руководство. Настройка столбцов представлений отчета).  
  
## См. также
<a id="see-also" class="xliff"></a>  
 [Caller / Callee View - Sampling Data](../profiling/caller-callee-view-sampling-data.md)  (Представление "Вызывающий/вызываемый" — данные выборки)  
 [Caller/Callee View - Instrumentation Data](../profiling/caller-callee-view-instrumentation-data.md)  (Представление "Вызывающий/вызываемый" — данные инструментирования)  
 [Caller/Callee View - NET Memory Instrumentation Data](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  (Представление "Вызывающий/вызываемый" — данные инструментирования памяти .NET)  
 [Caller/Callee View - .NET Memory Sampling Data](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  (Представление "Вызывающий/вызываемый" — данные выборки памяти .NET)  
 [Caller / Callee View -  Contention Data](../profiling/caller-callee-view-contention-data.md) (Представление "Вызывающий/вызываемый" — данные о конфликтах)
