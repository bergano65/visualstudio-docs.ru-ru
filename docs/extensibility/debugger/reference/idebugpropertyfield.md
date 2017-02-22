---
title: "IDebugPropertyField | Microsoft Docs"
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
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "Интерфейс IDebugPropertyField"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс предоставляет функции, позволяющие получать и устанавливать свойство.  
  
## Синтаксис  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## Примечания по реализации  
 Поставщик символов реализует этот интерфейс на одном и том же объекта, реализующего [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md).  Этот интерфейс специализация, которая поддерживает концепцию свойства в классе.  
  
## Замечания для вызывающих объектов  
 Используйте [QueryInterface](/visual-cpp/atl/queryinterface) получить этот интерфейс с  [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) если интерфейс  [GetKind](../Topic/IDebugField::GetKind.md) метод возвращает  `FIELD_KIND_PROP`.  
  
## Методы в том порядке Vtable  
 в дополнение к методам на [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и  [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейсы этот интерфейс реализуется следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Возвращает метод, который возвращает свойство.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Возвращает метод, который устанавливает свойство.|  
  
## Заметки  
 Свойство принцип управляемого кода и представляет метод, который обрабатывается как переменную.  Свойства не существуют в автономном C\+\+.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)