---
title: "StartTrackingContext | Microsoft Docs"
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
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Запуск контекста отслеживания.  
  
## Синтаксис  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### Параметры  
 \[входящий\] `intermediateDirectory`  
 Каталог, в который записывается журнал отслеживания.  
  
 \[входящий\] `taskName`  
 Определяет контекст отслеживания.  Это имя используется для создания файла журнала.  
  
## Возвращаемое значение  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) с установленным битом [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True), если был создан контекст отслеживания.  
  
## Требования  
 **Заголовок:** FileTracker.h