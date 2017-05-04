---
title: "ISetNextStatement::CanSetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ISetNextStatement.CanSetNextStatement
apilocation: scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# ISetNextStatement::CanSetNextStatement
Этот метод определяет, находится ли точка выполнения, который определяет следующую выписку кода для выполнения, можно задать в указанное расположение.  
  
## Синтаксис  
  
```  
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### Параметры  
 `pStackFrame`  
 \[in\] указатель на объект кадра стека.  
  
 `pCodeContext`  
 \[in\] указатель на объект контекста кода.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Следующий оператор можно обновить к заданному контексту кода.|  
|`S_FALSE`|Следующий оператор не может быть обновлен к заданному контексту кода.|  
  
## Заметки  
  
## См. также  
 [Интерфейс ISetNextStatement](../../winscript/reference/isetnextstatement-interface.md)