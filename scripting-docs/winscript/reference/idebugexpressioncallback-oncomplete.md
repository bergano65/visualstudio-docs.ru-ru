---
title: "IDebugExpressionCallBack::onComplete | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionCallBack.onComplete
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExpressionCallBack::onComplete"
ms.assetid: d0b89db3-38e7-44e0-93fe-60205f9149dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionCallBack::onComplete
Указывает, что вычисление выражений завершена.  
  
## Синтаксис  
  
```  
HRESULT onComplete();  
```  
  
#### Параметры  
 Этот метод не принимает параметры.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод вызывается при завершении вычисления выражений.  Метод `IDebugExpression::GetResultAsString` можно вызывать из этого обработчика событий.  
  
## См. также  
 [Интерфейс IDebugExpressionCallBack](../../winscript/reference/idebugexpressioncallback-interface.md)   
 [IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)