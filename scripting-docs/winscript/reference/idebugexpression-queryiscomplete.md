---
title: "IDebugExpression::QueryIsComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.QueryIsComplete
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::QueryIsComplete"
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::QueryIsComplete
Определяет, если операция завершена.  
  
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
|`S_OK`|Метод выполнен успешно, а операция завершения.|  
|`S_FALSE`|Операция все еще отложена.|  
  
## Заметки  
 Этот метод определяет, если операция завершена.  
  
## См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)