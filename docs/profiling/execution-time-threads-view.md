---
title: "Время выполнения (представление \"Потоки\") | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.execution
helpviewer_keywords: Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 91fda110b3bf73b59d7c9d7d8ff6f7226f9ec5fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="execution-time-threads-view"></a>Время выполнения (представление "Потоки")
Эти сегменты на временной шкале представления "Потоки" представляют время выполнения, когда поток активно выполняется в логическом ядре в системе.  
  
 Изменения в состоянии потока обнаруживаются с помощью событий переключения контекста ядра. Трассировка событий для Windows (ETW) фиксирует стеки выборки каждую миллисекунду. В очень коротких зеленых сегментах выборки могут отсутствовать. Таким образом, для некоторых коротких сегментов стек вызовов может не отображаться.  
  
 Если щелкнуть сегмент выполнения, в визуализаторе параллелизма отобразится стек выборки, ближайший к расположению щелчка. Положение этого стека выборки обозначается черной стрелкой (или курсором) над временной шкалой, а сам стек выборки отображается на вкладке **Текущее**.  
  
 Чтобы просмотреть традиционный профиль выборки для всех сегментов выполнения в текущем представлении, щелкните **Выполнение** в профиле видимой временной шкалы.  
  
## <a name="see-also"></a>См. также  
 [Отчет о профиле выполнения](../profiling/execution-profile-report.md)   
 [Представление потоков](../profiling/threads-view-parallel-performance.md)