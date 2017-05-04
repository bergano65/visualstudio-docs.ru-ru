---
title: "IDebugExpression::Start | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.Start
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::Start"
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::Start
Начинает оценку выражения.  
  
## Синтаксис  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### Параметры  
 `pdecb`  
 \[in\] метод обратного вызова для отображения, когда вычисление выражений завершена.  Если этот параметр `NULL`, никакие события не сгорены и клиент должен запроса состояние выражения с помощью `QueryIsComplete`.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Данный метод начинает оценку выражения.  
  
## См. также  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)