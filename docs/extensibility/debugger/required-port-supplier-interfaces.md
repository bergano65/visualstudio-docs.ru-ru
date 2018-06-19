---
title: Необходимые интерфейсы поставщика порта | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e34627effce5e2f0d1401da683536548a32d3f6e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128664"
---
# <a name="required-port-supplier-interfaces"></a>Требуемый порт интерфейсы поставщика
Необходимо реализовать поставщика порта [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейса.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Поскольку поставщика порта предоставляет портов, он также реализовать их. Таким образом он должен реализовать следующие интерфейсы:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Описывает порт и предназначенный для перечисления всех процессов, запущенных на порту.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Обеспечивает запуск и завершение процессов на порту.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Предоставляет механизм для программы, запущенные в контексте этого порта уведомлять его создание узла программы и удаления. Дополнительные сведения см. в разделе [узлов программы](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Предоставляет точку соединения для [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Порт поставщика операции  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) приемник получает уведомления, когда обработка и программы создаются и удаляются через порт. Порт, необходимое для отправки [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) при создании процесса и [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) при уничтожении процесса по порту. Порт также должен отправлять [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) при создании программы и [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) при уничтожении программы в процесс, запущенный на порт.  
  
 Порт обычно программа отправляет создавать и удалять события в ответ на [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) и [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) методы, соответственно.  
  
 Поскольку порт можно запустить и завершить процессы физических и логических программы, эти интерфейсы также должен быть реализован ядром отладки:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Описывает физические процесс. По крайней мере должны быть реализованы следующие методы:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Предоставляет способ для SDM для присоединения и отсоединения сам из процесса.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Описывает логические программы. По крайней мере должны быть реализованы следующие методы:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Предоставляет способ для SDM для присоединения к этой программе.  
  
## <a name="see-also"></a>См. также  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)