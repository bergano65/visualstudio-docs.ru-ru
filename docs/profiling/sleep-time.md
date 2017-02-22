---
title: "Время ожидания | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "Визуализатор параллелизма, Время ожидания"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Время ожидания
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эти сегменты на временной шкале связаны со временем блокировки, отнесенным к категории спящего режима.  Категория спящего режима подразумевает, что поток "добровольно" освободил логическое ядро и не выполняет никакую работу.  В этот момент поток был заблокирован в интерфейсе API, который визуализатор параллелизма интерпретирует как спящий режим.  К этой группе относятся такие интерфейсы API, как `Sleep()` и `SwitchToThread()`.  
  
## См. также  
 [Представление потоков](../profiling/threads-view-parallel-performance.md)