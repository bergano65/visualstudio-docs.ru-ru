---
title: "IDebugCoreServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "Интерфейс IDebugCoreServer2"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс используется для представления и получать сведения с сервера на компьютере в сети.  
  
## Синтаксис  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## Примечания по реализации  
 Visual Studio реализующий этот интерфейс, чтобы представить сервер.  Каждый экземпляр Visual Studio создает экземпляр этого интерфейса.  
  
## Замечания для вызывающих объектов  
 Пользовательский поставщик порта получает это при вызове интерфейса [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Отладчик может получить этот интерфейс косвенно через вызов [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) \(которое возвращает  [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)интерфейс, наследуемый от  `IDebugCoreServer2`\).  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugCoreServer2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)|Возвращает имя и атрибуты компьютера.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Получает имя компьютера.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Возвращает поставщика порта, который существует на компьютере.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Получает порт, уже существует на компьютере.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Создает перечислитель для всех портов на компьютере.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Создает перечислитель для всех поставщиков портов на компьютере.|  
|[GetMachineUtilities\_V7](../Topic/IDebugCoreServer2::GetMachineUtilities_V7.md)|Получает служебные программы компьютера для компьютера.|  
  
## Заметки  
 Этот интерфейс также используется Visual Studio, чтобы просмотреть процессами, запущенными на компьютерах в сети.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)