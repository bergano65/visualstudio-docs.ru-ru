---
title: IDebugProgram2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392d9bd350d6207e6725c31c659a6edf1518a807
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122604"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Этот интерфейс представляет программу, которая выполняется в процессе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) и поставщика пользовательский порт реализуют этот интерфейс для представления программы в процессе. Диспетчер сеансов отладки (SDM) также реализует этот интерфейс для предоставления сведений о [присоединение](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) событие возвращает этот интерфейс для новой программы. Этот интерфейс также используется как параметр для многих методов на нескольких интерфейсах.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProgram2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Перечисляет потоков, работающих в этой программе.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Возвращает имя программы.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Получает процесс, в работе программы.|  
|[Завершение](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Завершает этой программы.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Присоединяет к этой программе.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Определяет, если в программе можно отсоединить отладчик (DE).|  
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Отсоединяет отладчик от этой программы.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Возвращает глобальный уникальный идентификатор для этой программы.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Получает программный свойства.|  
|[Выполнение](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает выполнение программы в остановленном состоянии. Предыдущее состояние выполнения очищается.|  
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает выполнение программы в остановленном состоянии. Предыдущее состояние выполнения сохраняется.|  
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Запросы, что эта программа остановить выполнение следующего время один из его потоков выполняется код.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Возвращает имя и идентификатор модуля отладки (DE), выполнение программы.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Перечисляет контекстов для заданной позиции в файле исходного кода.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Возвращает байт памяти для этой программы.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Возвращает поток Дизассемблированный код для этой программы или часть этой программы.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Перечисляет модули, эта программа загрузки и выполнения.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Получает обновления изменить и продолжить (ENC) для этой программы.<br /><br /> Пользовательские отладки ядра не реализует этот метод (всегда должны возвращать `E_NOTIMPL`).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Перечисляет путей кода программы.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Записывает в файл дампа.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Примечания  
 Программы — это контейнер потока, в конкретной архитектуры во время выполнения, на выполнение, пока процесс состоит из одной или нескольких программ.  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Присоединение](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)