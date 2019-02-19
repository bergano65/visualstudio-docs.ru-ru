---
title: Время выполнения (представление "Потоки") | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4306e030c2f48d87b12ba6338a847dc9e9aa892
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2019
ms.locfileid: "54766246"
---
# <a name="execution-time-threads-view"></a>Время выполнения (представление "Потоки")
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эти сегменты на временной шкале представления "Потоки" представляют время выполнения, когда поток активно выполняется в логическом ядре в системе.  
  
 Изменения в состоянии потока обнаруживаются с помощью событий переключения контекста ядра. Трассировка событий для Windows (ETW) фиксирует стеки выборки каждую миллисекунду. В очень коротких зеленых сегментах выборки могут отсутствовать. Таким образом, для некоторых коротких сегментов стек вызовов может не отображаться.  
  
 Если щелкнуть сегмент выполнения, в визуализаторе параллелизма отобразится стек выборки, ближайший к расположению щелчка. Положение этого стека выборки обозначается черной стрелкой (или курсором) над временной шкалой, а сам стек выборки отображается на вкладке **Текущее**.  
  
 Чтобы просмотреть традиционный профиль выборки для всех сегментов выполнения в текущем представлении, щелкните **Выполнение** в профиле видимой временной шкалы.  
  
## <a name="see-also"></a>См. также раздел  
 [Отчет о профиле выполнения](../profiling/execution-profile-report.md)   
 [Представление потоков](../profiling/threads-view-parallel-performance.md)
