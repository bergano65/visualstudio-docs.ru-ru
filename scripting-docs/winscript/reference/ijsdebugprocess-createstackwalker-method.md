---
title: "Метод IJsDebugProcess::CreateStackWalker | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateStackWalker
apilocation: jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugProcess::CreateStackWalker
Фабричный метод для средства обхода стека.  
  
## Синтаксис  
  
```  
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### Параметры  
 `threadId`  
 \[in\] Идентификатор потока.  
  
 `ppStackWalker`  
 \[out\] Новый объект просмотра стека.  
  
## Возвращаемое значение  
  
## Заметки  
 Возвращает E\_JsDEBUG\_UNKNOWN\_THREAD, если поток не имеет JavaScript на нем.  Этот метод может быть вызван, когда процесс целевого объекта останавливается.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)