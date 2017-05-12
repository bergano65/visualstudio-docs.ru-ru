---
title: "IEnumDebugExpressionContexts::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Skip"
ms.assetid: 3498cbb5-8581-4dcd-b016-e86b049c7831
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Skip
Пропустить указанное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] количество сегментов в последовательности перечисления, которые нужно пропустить.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод пропустить указанное количество сегментов в последовательности перечисления.  
  
## См. также  
 [Интерфейс IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)