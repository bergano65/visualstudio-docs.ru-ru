---
title: "IDebugPort2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPort2"
helpviewer_keywords: 
  - "Интерфейс IDebugPort2"
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPort2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет порт отладки на компьютере.  
  
## Синтаксис  
  
```  
IDebugPort2 : IUnknown  
```  
  
## Примечания по реализации  
 Пользовательский поставщик порта, реализующий этот интерфейс, чтобы представить порт отладки на компьютере.  
  
 Если порт поддерживает отправлять события порта, он также должен реализовывать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс для поддержки  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс, который, в свою очередь, предоставляющий  [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейс.  
  
## Замечания для вызывающих объектов  
 Вызовы [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) OR  [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) возвращение этот интерфейс, представляющий порт.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugPort2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Возвращает имя порта.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Возвращает идентификатор порта.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Возвращает запрос, используемый для создания порт \(при наличии\).|  
|[GetPortSupplier](../Topic/IDebugPort2::GetPortSupplier.md)|Возвращает поставщика порта для данного порта.|  
|[GetProcess](../Topic/IDebugPort2::GetProcess.md)|Возвращает интерфейс к процессу заданный идентификатор процесса.|  
|[EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)|Перечисляет все процессы, выполняющиеся на порт.|  
  
## Заметки  
 Локальный порт предоставляет доступ ко всем процессам и программам, выполняющимся на локальном компьютере.  Другие порты могут представлять последовательного соединения с помощью метода с префиксом tail в устройство CE\-основанному окнами или сетевого подключения к компьютеру non\-DCOM.  `IDebugPort2` интерфейс используется для поиска имени и идентификатора порта перечислить все процессы, выполняющиеся на порт, и предоставить возможности для запуска и окончания процессов на порт.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)