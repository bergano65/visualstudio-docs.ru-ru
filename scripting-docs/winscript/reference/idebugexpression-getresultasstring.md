---
title: "IDebugExpression::GetResultAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsString"
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsString
Возвращает результат оценки выражений в виде строки, а возвращаемое значение операции.  
  
## Синтаксис  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### Параметры  
 `phrResult`  
 \[out\] возвращаемое значение операции.  
  
 `pbstrResult`  
 \[out\] результат оценки выражений.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция все еще отложена.|  
  
## Заметки  
 Этот метод возвращает результат оценки выражений в виде строки, а `HRESULT` операции.  
  
 Этот метод возвращает `S_ОК` и `phrResult` возвращает `E_ABORT` если `Abort` прерывает операцию.  
  
## См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)