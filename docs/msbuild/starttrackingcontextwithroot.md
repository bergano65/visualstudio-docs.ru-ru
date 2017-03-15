---
title: "StartTrackingContextWithRoot | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Запуск контекста отслеживания с помощью файла ответов с указанием корневого маркера.  
  
## Синтаксис  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### Параметры  
 \[входящий\] `intermediateDirectory`  
 Каталог, в который записывается журнал отслеживания.  
  
 \[входящий\] `taskName`  
 Определяет контекст отслеживания.  Это имя используется для создания файла журнала.  
  
 \[входящий\] `rootMarkerResponseFile`  
 Путь файла ответа, содержащего корневой маркер.  Имя корневой папки используется для группирования всех отслеживаемых сведений контекста вместе.  
  
## Возвращаемое значение  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) с установленным битом [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True), если был создан контекст отслеживания.  
  
## Требования  
 **Заголовок:** FileTracker.h  
  
## См. также  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)