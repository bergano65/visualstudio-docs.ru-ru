---
title: "Метод IJsDebugStackWalker::GetNext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugStackWalker::GetNext
Получает следующий кадр.  
  
## Синтаксис  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### Параметры  
 `ppFrame`  
 \[out\] Объект, представляющий кадр стека.  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает E\_JsDEBUG\_OUTSIDE\_OF\_VM, если больше нет кадров стека, которые необходимо перечислить  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)