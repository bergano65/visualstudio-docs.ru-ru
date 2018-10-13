---
title: IDebugProcess2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5d1fcdb6df958a62ed23b3bc7e812e1f4a7e15f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218781"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет процесс, работающий с портом. Если порт локального порта, затем `IDebugProcess2` обычно представляет физического процесса на локальном компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщиком пользовательский порт, для управления программами как группу. Этот интерфейс должен реализовываться поставщика порта.  
  
 Модуль отладки также реализует этот интерфейс, если он поддерживает запуск программы через [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Этот интерфейс называется главным образом диспетчер отладки сеансов (SDM) для взаимодействия с группой программы, указанные в этом процессе.  
  
 Вызовите [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) или [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) для получения этого интерфейса. Этот интерфейс также возвращается путем вызова `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProcess2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Возвращает описание процесса.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Перечисляет программы, которые содержатся в этом процессе.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Возвращает заголовок, понятное имя или имя файла процесса.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Получает экземпляр этого процесса, запущенного на машины Server.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Завершает процесс.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Присоединяет к процессу.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Определяет, если SDM можно отсоединить процесс.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Отсоединяет отладчик от процесса.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Получает системный идентификатор процесса.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Получает глобальный уникальный идентификатор для этого процесса.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [УСТАРЕЛО]|Получает имя сеанса, который является отладка процесса.<br /><br /> [УСТАРЕЛО. СЛЕДУЕТ ВСЕГДА ВОЗВРАЩАЮТ `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Перечисляет потоков, выполняемых в процессе.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Запрашивает выполнение кода в этот процесс остановки следующей программы.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Получает порт, который выполняется этот процесс.|  
  
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

