---
title: "IEnumDebugExpressionContexts::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Next
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Next"
ms.assetid: aa223b0b-f7c1-4368-a59e-677e60133baf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Next
Извлекает заданное количество сегментов в последовательности перечисления.  
  
## Синтаксис  
  
```  
HRESULT Next(  
   ULONG                      celt,  
   IDebugExpressionContext**  ppdec,  
   ULONG*                     pceltFetched  
);  
```  
  
#### Параметры  
 `celt`  
 \[in\] число сегментов, который необходимо извлечь.  
  
 `ppdec`  
 \[out\] возвращает массив интерфейсов `IDebugExpressionContext`, представляющий восстанавливаемая сегменты.  
  
 `pceltFetched`  
 \[out\] фактическое количество сегментов выбирается перечислителем.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод извлекает заданное количество сегментов в последовательности перечисления.  
  
## См. также  
 [Интерфейс IEnumDebugExpressionContexts](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)