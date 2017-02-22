---
title: "BP_LOCATION_CODE_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_ADDRESS"
helpviewer_keywords: 
  - "Структура BP_LOCATION_CODE_ADDRESS"
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_CODE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Описывает местоположение точки останова по адресу в коде.  
  
## Синтаксис  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## Члены  
 `bstrContext`  
 Контекст точки останова, как правило, имя метода или функции, как показано в стеке вызова.  
  
 `bstrModuleUrl`  
 URL\-адрес модуля, в котором содержится точка останова.  
  
 `bstrFunction`  
 Имя функции, содержащей точку останова.  
  
 `bstrAddress`  
 Адрес точки останова, анализируется средством оценки выражений, чтобы привязать его к [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объект.  
  
## Заметки  
 Эта структура элемент [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структура как часть соединения.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)