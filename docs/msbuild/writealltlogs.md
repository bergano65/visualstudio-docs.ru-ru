---
title: "WriteAllTLogs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "WriteAllTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteAllTLogs"
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# WriteAllTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Записывает журналы отслеживания для всех контекстов и потоков.  
  
## Синтаксис  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)