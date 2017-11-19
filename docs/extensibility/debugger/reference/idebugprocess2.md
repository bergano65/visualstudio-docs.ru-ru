---
title: "IDebugProcess2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2
helpviewer_keywords: IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8b349bee09f068a5777ecc212223c36951236ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2"></a>IDebugProcess2
Этот интерфейс представляет процесс, запущенный на порт. Если порт находится локальный порт, затем `IDebugProcess2` обычно представляет физического процесса на локальном компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется пользовательский порт поставщика для управления программами в группу. Этот интерфейс должен быть реализован поставщиком порта.  
  
 Модуль отладки реализует этот интерфейс, если он поддерживает запуск программы через [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс называется главным образом диспетчером сеанса отладки (SDM) для взаимодействия с группой программы, указанные в этом процессе.  
  
 Вызовите [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) или [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) получить этот интерфейс. Этот интерфейс также возвращается путем вызова `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProcess2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Возвращает описание процесса.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Перечисляет программы, которые содержатся в этом процессе.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Возвращает заголовок, понятное имя или имя файла процесса.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Получает экземпляр этого процесса, запущенного на машины Server.|  
|[Завершение](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Завершает процесс.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Присоединяет к процессу.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Определяет, если SDM можно отсоединить процесс.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Отсоединяет отладчик от процесса.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Получает идентификатор процесса системы.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Возвращает глобальный уникальный идентификатор для данного процесса.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [УСТАРЕЛО]|Возвращает имя сеанса, отлаживаемого процесса.<br /><br /> [НЕ РЕКОМЕНДУЕТСЯ. СЛЕДУЕТ ВСЕГДА ВОЗВРАЩАЮТ `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Перечисляет потоков, выполняемых в процессе.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Запрашивает выполнение кода в этот процесс остановки следующей программы.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Возвращает номер порта, этот процесс.|  
  
## <a name="remarks"></a>Примечания  
 `IDebugProcess2` Содержит один или несколько [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейсов.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)