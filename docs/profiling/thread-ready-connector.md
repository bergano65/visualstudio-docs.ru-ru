---
title: "Соединитель готовности потока | Microsoft Docs"
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
  - "vs.cv.threads.timeline.threadready"
helpviewer_keywords: 
  - "Визуализатор параллелизма, Поток готов"
ms.assetid: 68e1ec38-4b10-4b01-b32f-6c9a00b2443c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Соединитель готовности потока
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если щелкнуть блокирующий сегмент для просмотра стека вызова и разблокирующего его стека, может также отобразиться соединитель готовности потока.  Если разблокирующее событие происходит в другом потоке текущего процесса, соединитель готовности потока визуально обозначает поток и сегмент выполнения, который позволит возобновить выполнение заблокированного потока.