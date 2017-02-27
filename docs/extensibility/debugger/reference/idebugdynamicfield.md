---
title: "IDebugDynamicField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDynamicField"
helpviewer_keywords: 
  - "Интерфейс IDebugDynamicField"
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDynamicField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет тип переменной.  
  
## Синтаксис  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется поставщиками символов как базовый класс для любого типа, который может быть определена во время выполнения.  Это только для управляемого кода.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс представляет базовый класс, из которого больше специализировал интерфейсов может быть получено.  
  
## Методы в том порядке Vtable  
 Этот интерфейс не предоставляет никаких методов за исключением тех из наследуемых `IDebugField`.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)