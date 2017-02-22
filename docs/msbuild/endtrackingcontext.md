---
title: "EndTrackingContext | Microsoft Docs"
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
  - "EndTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "EndTrackingContext"
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# EndTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Заканчивает текущий контекст отслеживания.  
  
## Синтаксис  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## Возвращаемое значение  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) с набором битов [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True), если контекст отслеживания был завершен.  
  
## Требования  
 **Заголовок:** FileTracker.h  
  
## См. также  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)