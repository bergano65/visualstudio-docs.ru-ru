---
title: "IDebugExpression::GetResultAsDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsDebugProperty
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsDebugProperty"
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsDebugProperty
Возвращает результат оценки выражений в качестве свойства отладки и возвращаемое значение операции.  
  
## Синтаксис  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### Параметры  
 `phrResult`  
 \[out\] возвращаемое значение операции.  
  
 `ppdp`  
 \[out\] свойства отладки для выражения.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_PENDING`|Операция все еще отложена.|  
  
## Заметки  
 Этот метод возвращает результат вычисления выражения, как `IDebugProperty` и `HRESULT` операции.  
  
 Этот метод возвращает `S_ОК` и `phrResult` возвращает `E_ABORT` если `Abort` прерывает операцию.  
  
## См. также  
 [Интерфейс IDebugExpression](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)