---
title: "SetThreadCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SetThreadCount"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SetThreadCount"
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# SetThreadCount
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает глобальное число потоков и назначает это число текущему потоку.  
  
## Синтаксис  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### Параметры  
 \[входящий\] `threadCount`  
 Количество используемых потоков.  
  
## Возвращаемое значение  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) с набором битов [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True), если число потоков было обновлено.  
  
## Требования  
 **Заголовок:** FileTracker.h