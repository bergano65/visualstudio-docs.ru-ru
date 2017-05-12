---
title: "Метод IJsDebugFrame::GetStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Метод IJsDebugFrame::GetStackRange
Возвращает диапазон абсолютных адресов логического фрейма стеков JavaScript.  
  
## Синтаксис  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### Параметры  
 `pStart`  
 \[out\] Самый нижний указатель на кадр стека.  
  
 `pEnd`  
 \[out\] Самый верхний указатель на кадр стека.  
  
## Возвращаемое значение  
  
## Заметки  
 Этот метод полезен для соединения вместе перемежаемых трассировок стека вместе с множественными средами выполнения.  Начальные и конечные указатели стека могут включать несколько кадров стека физического компьютера \(для интерпретированных кадров среды выполнения JavaScript\). Начальный и конечный стеки\> меняются от максимальных к минимальным адресам.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)