---
title: "ResumeTracking | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Возобновляет отслеживание в текущем контексте.  
  
## Синтаксис  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## Возвращаемое значение  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) с набором битов [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True), если отслеживание было возобновлено.  [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True) возвращается, если не удалось возобновить отслеживание, поскольку контекст был недоступен.  
  
## Требования  
 **Заголовок:** FileTracker.h  
  
## См. также  
 [SuspendTracking](../msbuild/suspendtracking.md)