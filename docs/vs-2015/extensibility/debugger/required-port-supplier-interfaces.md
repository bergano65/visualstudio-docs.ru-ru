---
title: Необходимые интерфейсы поставщика порта | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 485c295e7258f09aaf4114d5945f8136057447e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782808"
---
# <a name="required-port-supplier-interfaces"></a>Интерфейс поставщика необходимого порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Поставщика порта необходимо реализовать [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Поскольку поставщика порта предоставляет порты, он также реализовать их. Таким образом он должен реализовывать следующие интерфейсы:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Описывает порт и можно перечислить все процессы, запущенные на порт.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Предоставляет для запуска и завершения процессов в порт.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Предоставляет механизм для программ, работающих в контексте этого порта уведомлять его создание узла программы и удаления. Дополнительные сведения см. в разделе [узлы программы](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Предоставляет точку подключения для [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Операции поставщика порта  
 [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) приемник получает уведомления, когда обработка и программы создаются и удаляются через порт. Для отправки требуется порт [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) при создании процесса и [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) при уничтожении процесса на порте. Порт для отправки также требуется [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) при создании программы и [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) при уничтожении программы в процесс, выполняющийся в порт.  
  
 Порт обычно программа отправляет создавать и удалять события в ответ на [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) и [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) методы, соответственно.  
  
 Так как порт можно запустить и завершить процессы физических и логических программы, необходимо реализовать эти интерфейсы ядром отладки:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Описывает процесс физического. По крайней мере должны быть реализованы следующие методы:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Предоставляет способ для SDM, подключать и отключать сам из процесса.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Описывает логические программы. По крайней мере должны быть реализованы следующие методы:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Предоставляет способ для SDM для присоединения к этой программе.  
  
## <a name="see-also"></a>См. также  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)

