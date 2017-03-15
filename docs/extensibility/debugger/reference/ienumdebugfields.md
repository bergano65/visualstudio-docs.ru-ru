---
title: "IEnumDebugFields | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "Интерфейс IEnumDebugFields"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет коллекцию объектов реализация IDebugField интерфейс.  
  
## Синтаксис  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется поставщиком символов для предоставления наборы объектов, которые реализуют IDebugField интерфейс.  Обратите внимание, что это не стандартного перечисления модели COM из\-за присутствию [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) метод.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс возвращается by [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md) и  [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).  
  
## Методы в том порядке Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Извлекает следующий набор IDebugField объекты из перечисления.|  
|[Пропустить](../Topic/IEnumDebugFields::Skip.md)|Пропустить указанное количество записей.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Сбросит перечисление к первой записи.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Извлекает число записей в перечислении.|  
  
## Заметки  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)