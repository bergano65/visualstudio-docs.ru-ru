---
title: "BP_LOCATION_CODE_FILE_LINE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_FILE_LINE"
helpviewer_keywords: 
  - "Структура BP_LOCATION_CODE_FILE_LINE"
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_CODE_FILE_LINE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Содержит данные для расположения точки останова по определенной линии в исходном файле кода.  
  
## Синтаксис  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## Члены  
 `bstrContext`  
 Контекст точки останова, как правило, имя метода или функции, как показано в стеке вызова.  
  
 `pDocPos`  
 IDebugDocumentPosition2 объект, представляющий позицию документа точки останова.  
  
## Заметки  
 Эта структура элемент [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структура как часть соединения.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)