---
title: "IDebugMemoryContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2"
helpviewer_keywords: 
  - "Интерфейс IDebugMemoryContext2"
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет позицию в адресном пространстве компьютера, на котором выполняется отлаживаемый программы.  
  
## Синтаксис  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы представлять адрес в памяти.  
  
## Замечания для вызывающих объектов  
 Вызов [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) OR  [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) возвращает данный интерфейс.  Кроме того, вызовы [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) и  [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) примененные новые копии этого интерфейса, возвращаемые после соответствующей арифметической операции.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugMemoryContext2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Получает отображаемое для пользователя имя для данного контекста.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Получает сведения, описывающие этот контекст.|  
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Добавляет указанное значение на адрес текущего контекста для создания нового контекста.|  
|[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Вычитает указанное значение из адреса текущего контекста для создания нового контекста.|  
|[Сравнение](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Сравнивает 2 контекста способом, отображаемом by флаги сравнения.|  
  
## Заметки  
 Visual Studio **Память** вызовы окна  [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) доступ  `IDebugMemoryContext2` интерфейс, который содержит вычисленное выражение, используемый для адреса памяти.  Этот контекст затем передается [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и  [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md) указать адрес для чтения или записи.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../Topic/IDebugMemoryBytes2::WriteAt.md)