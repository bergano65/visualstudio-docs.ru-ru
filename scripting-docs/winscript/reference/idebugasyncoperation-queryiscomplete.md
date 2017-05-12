---
title: "IDebugAsyncOperation::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugAsyncOperation.QueryIsComplete
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugAsyncOperation::QueryIsComplete"
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation::QueryIsComplete
Определяет, если операция отладка завершена.  
  
## Синтаксис  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Операция завершена.|  
|`S_FALSE`|Операция не завершена.|  
  
## Заметки  
 Этот метод определяет, если операция отладка завершена.  
  
## См. также  
 [Интерфейс IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)