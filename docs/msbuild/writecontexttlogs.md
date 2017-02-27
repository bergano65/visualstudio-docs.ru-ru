---
title: "WriteContextTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteContextTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteContextTLogs"
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteContextTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Записывает файлы журналов для текущего контекста.  
  
## Синтаксис  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### Параметры  
 \[входящий\] `intermediateDirectory`  
 Каталог, в который записывается журнал отслеживания.  
  
 \[входящий\] `tlogRootName`  
 Корень имени файла журнала.  
  
## Возвращаемое значение  
 [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) с установленным битом [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True), если был создан контекст отслеживания.  
  
## Требования  
 **Заголовок:** FileTracker.h  
  
## См. также  
 [WriteAllTLogs](../msbuild/writealltlogs.md)