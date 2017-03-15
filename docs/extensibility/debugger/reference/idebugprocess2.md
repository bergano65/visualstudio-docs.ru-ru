---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "Интерфейс IDebugProcess2"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс представляет процесс на порт.  Если порт локальный порт, `IDebugProcess2` обычно представляет физический процесс на локальном компьютере.  
  
## Синтаксис  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется пользовательским поставщиком порта для управления программы, таких как группа.  Этот интерфейс должен быть реализован поставщиком порта.  
  
 Отладчик также реализует этот интерфейс, если он поддерживает запуск программы до конца [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## Замечания для вызывающих объектов  
 Этот интерфейс, вызывается основным сеанса отладки \(SDM\) диспетчер для взаимодействия с группой в составе программы, заданные в этом процессе.  
  
 Вызов [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) OR  [GetProcess](../Topic/IDebugPort2::GetProcess.md) получить этот интерфейс.  Этот интерфейс также возвращается путем вызова `IDebugEngineLaunch2::LaunchSuspended`.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugProcess2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Возвращает описание процесса.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Перечисляет программы, содержащихся в данном процессе.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Возвращает имя, понятное имя или имя файла процесса.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Возвращает экземпляр сервера компьютера этот процесс запущен.|  
|[Завершить](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Завершает процесс.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Вложение в процесс.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Определяет, SDM, наконец, процесс может удалить.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Наконец удаляет отладчик из процесса.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Получает идентификатор процесса системы.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Возвращает идентификатор guid для этого процесса.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[НЕРЕКОМЕНДУЕМЫЙ\]|Возвращает имя сеанса, процесс отладки.<br /><br /> \[НЕРЕКОМЕНДУЕМЫЙ.  ВСЕГДА ВОЗВРАЩАТЬ `E_NOTIMPL`.\]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Перечисляет потоков в процессе.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Запросы, которые код следующей программы работающим в этом стопе процесса.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Получает порт, что процесс запущен.|  
  
## Заметки  
 `IDebugProcess2` содержит один или несколько  [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейсы.  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../Topic/IDebugPort2::GetProcess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)