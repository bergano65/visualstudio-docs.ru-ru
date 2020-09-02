---
title: IDebugProcess2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68f1693bbbda9bbf7622c2378799db4a342be7a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187968"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет процесс, выполняемый в порте. Если порт является локальным портом, `IDebugProcess2` обычно он представляет физический процесс на локальном компьютере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется поставщиком пользовательского порта для управления программами как группой. Этот интерфейс должен быть реализован поставщиком порта.  
  
 Модуль отладки также реализует этот интерфейс, если он поддерживает запуск программы через [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс вызывается главным образом диспетчером отладки сеансов (SDM) для взаимодействия с группой программ, идентифицированных в этом процессе.  
  
 Чтобы получить этот интерфейс, вызовите метод [внутрипроцессного](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) или [обработки](../../../extensibility/debugger/reference/idebugport2-getprocess.md) . Этот интерфейс также возвращается путем вызова метода `IDebugEngineLaunch2::LaunchSuspended` .  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProcess2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Возвращает описание процесса.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Перечисляет программы, содержащиеся в этом процессе.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Возвращает заголовок, понятное имя или имя файла процесса.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Возвращает экземпляр сервера-компьютера, на котором выполняется этот процесс.|  
|[Завершение](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Завершает процесс.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Присоединяется к процессу.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Определяет, может ли SDM отсоединить процесс.|  
|[Отсоединить](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Отсоединяет отладчик от процесса.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Возвращает идентификатор системного процесса.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Возвращает глобальный уникальный идентификатор для этого процесса.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> НЕ рекомендуется|Возвращает имя сеанса, в котором выполняется отладка процесса.<br /><br /> Не рекомендуется. ДОЛЖЕН всегда возвращать `E_NOTIMPL` .]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Перечисляет потоки, выполняющиеся в процессе.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Запрашивает, что следующая программа, выполняющая код в этом процессе, останавливается.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Возвращает порт, на котором выполняется этот процесс.|  
  
## <a name="remarks"></a>Remarks  
 `IDebugProcess2`Содержит один или несколько интерфейсов [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: Мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [лаунчсуспендед](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Очеред](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Журнале](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Журнале](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
