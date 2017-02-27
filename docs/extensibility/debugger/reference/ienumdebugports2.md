---
title: "IEnumDebugPorts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2"
helpviewer_keywords: 
  - "IEnumDebugPorts2"
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет портам компьютера или поставщика порта.  
  
## Синтаксис  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта, реализующий этот интерфейс, чтобы представлять список портов, созданных поставщиком.  Visual Studio реализует этот интерфейс для поддержки собственного поставщика порта.  
  
## Замечания для вызывающих объектов  
 Вызов [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) получить этот интерфейс, представляющий список портов, созданных поставщиком порта.  Вызов [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) получить этот интерфейс, представляющий список портов, которые были сохранены на диске.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugPorts2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Получает заданное число портов в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Пропустить указанное количество портов в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../Topic/IEnumDebugPorts2::GetCount.md)|Получает число портов в перечислителе.|  
  
## Заметки  
 Visual Studio использует этот интерфейс, чтобы заполнить список портов используемых для вложения к процессу.  
  
 Отладчик обычно не использует этот интерфейс.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)