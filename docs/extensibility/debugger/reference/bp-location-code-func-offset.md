---
title: "BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_FUNC_OFFSET"
helpviewer_keywords: 
  - "Структура BP_LOCATION_CODE_FUNC_OFFSET"
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_CODE_FUNC_OFFSET
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает расположение смещения точки останова в функции в коде.  
  
## Синтаксис  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## Члены  
 `bstrContext`  
 Контекст точки останова, как правило, имя метода или функции, как показано в стеке вызова.  
  
 `pFuncPos`  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) объект, описывающий имя функции и относительное положение с начала функции.  
  
## Заметки  
 Эта структура элемент [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структура как часть соединения.  
  
 `pFuncPos` элемент показано, как установить точку останова в функции.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)