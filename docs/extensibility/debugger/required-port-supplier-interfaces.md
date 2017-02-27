---
title: "Требуемый порт интерфейса поставщика | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "поставщикам портов, требуемых интерфейсов"
  - "отладка [пакет SDK для отладки], порт поставщиков"
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Требуемый порт интерфейса поставщика
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Поставщик порта должен реализовать [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс.       [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Поскольку порты, оно содержит поставщика порта должны также реализовать их.  Поэтому он должен реализовывать следующие интерфейсы:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Описывает порт и может перечислить все процессы, выполняющиеся на порт.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Предоставляет для запуска и окончания процессов на порт.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Предоставляет механизм для программ, выполняемых в контексте этого порта для уведомления его создания и удаления узлов программы.  Дополнительные сведения см. в разделе [Программа узлов](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Предоставляет точку подключения для [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## Операция поставщика порта  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) приемник получает уведомления, когда процесс и программы создаются и уничтожаются с номером порта.  Порт требуется отправлять [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) при создании процесс и  [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) если процесс уничтожается по порту.  Также требуется отправлять порт [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) при создании программы и  [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) когда программа разрушена в ходе процесса на порт.  
  
 Порт обычно отправляет программа создает и удаляет события в ответ на [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) и  [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) методы соответственно.  
  
 Поскольку порт может начинаться и заканчиваться и физические и логические процессы программы, эти интерфейсы также должны быть реализованы модулем отладки.  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Описывает физические процесс.  Как минимум, необходимо реализовать следующие методы:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Предоставляет способ для SDM вложение и, наконец, удаляется из процесса.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Описывает логические программу.  Как минимум, необходимо реализовать следующие методы:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Предоставляет способ для SDM вложить в этой программе.  
  
## См. также  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)