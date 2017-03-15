---
title: "IDebugPortSupplier3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "Интерфейс IDebugPortSupplier3"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс позволяет вызывающему объекту указать, следует ли поставщик порта может сохранять портов \(путем записи их на диск\) между вызовами отладчика, а затем получить список этих сохраненных порты.  
  
## Синтаксис  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта, реализующий этот интерфейс, чтобы поддерживать сохранить или сохранить данные порта на диск.  Этот интерфейс должен быть реализован в одном объекте как [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс.  
  
## Замечания для вызывающих объектов  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugPortSupplier2` интерфейс для получения этого интерфейса.  
  
## Методы в том порядке Vtable  
 Помимо методов, наследуемых из [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс этот интерфейс поддерживает следующие функции:  
  
|Метод|Описание|  
|-----------|--------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Возвращает значение, указывающее, является ли поставщик порта может сохраняться портов \(путем записи их на диск\) между вызовами отладчика.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Возвращает объект, который может использоваться для перечисления, пока все порты, которые были записаны на диск этим поставщиком порта.|  
  
## Заметки  
 Если поставщик порта может сохраняться портов через вызовы, он должен реализовать данный интерфейс.  Порты должны быть загружены, когда создается и записывают поставщик порта на диск, когда разрушают поставщика порта.  
  
 Отладчик не взаимодействует с поставщиком порта и не будет содержать никаких использование этого интерфейса.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)