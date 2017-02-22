---
title: "IEnumDebugAddresses | Microsoft Docs"
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
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "Интерфейс IEnumDebugAddresses"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет коллекцию объектов реализация [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  
  
## Синтаксис  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется поставщиком символов для предоставления наборы объектов, которые реализуют [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.  Обратите внимание, что это не стандартного перечисления модели COM из\-за присутствию [GetCount](../Topic/IEnumDebugAddresses::GetCount.md) метод.  
  
## Замечания для вызывающих объектов  
 Этот интерфейс возвращается by [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) и  [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md).  
  
## Методы в том порядке Vtable  
 Этот интерфейс реализует следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../Topic/IEnumDebugAddresses::Next.md)|Извлекает следующий набор [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекты из перечисления.|  
|[Пропустить](../Topic/IEnumDebugAddresses::Skip.md)|Пропустить указанное количество записей.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Сбросит перечисление к первой записи.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Извлекает копию текущего перечисления.|  
|[GetCount](../Topic/IEnumDebugAddresses::GetCount.md)|Извлекает число записей в перечислении.|  
  
## Заметки  
 Этот интерфейс обычно используется обработчиком отладки, чтобы помочь определить соответствующий адрес для передачи средству оценки выражений.  
  
## Требования  
 Заголовок: sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)