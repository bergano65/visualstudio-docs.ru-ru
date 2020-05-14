---
title: IDebugПрограмма2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722716"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Этот интерфейс представляет собой программу, которая работает в процессе.

## <a name="syntax"></a>Синтаксис

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) и поставщик пользовательских портов реализуют этот интерфейс, чтобы представлять программу в процессе. Менеджер отладки сеанса (SDM) также реализует этот интерфейс для предоставления информации [для присоединения.](../../../extensibility/debugger/reference/idebugprogram2-attach.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 [Событие IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) возвращает этот интерфейс для новой программы. Этот интерфейс также используется в качестве параметра для многих методов на нескольких интерфейсах.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProgram2`.

|Метод|Описание|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Перечисляет потоки, которые работают в этой программе.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Получает название программы.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Получает процесс, в который работает эта программа.|
|[Завершить](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Прекращает эту программу.|
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Прикрепляется к этой программе.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Определяет, может ли отладка двигателя (DE) отсоединиться от программы.|
|[Detach](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Отсоединяет отладчика из этой программы.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Получает глобально уникальный идентификатор для этой программы.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Получает свойства программы.|
|[Выполнить](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Продолжает запуск этой программы из остановленного состояния. Любое предыдущее состояние выполнения очищается.|
|[Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Продолжает запуск этой программы из остановленного состояния. Любое предыдущее состояние выполнения сохраняется.|
|[Шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Просит, чтобы эта программа прекратила выполнение при следующем запуске кода.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Получает имя и идентификатор движка отладки (DE), который работает с этой программой.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Перечисляет контексты кода для данной позиции в исходном файле.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Получает байты памяти для этой программы.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Получает поток разборок для этой программы или части этой программы.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Перечисляет модули, которые загружается и исполняется эта программа.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Получает обновление edit and Continue (ENC) для этой программы.<br /><br /> Пользовательский отладка двигателя не реализует этот `E_NOTIMPL`метод (он всегда должен вернуться ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Перечисляет пути кода этой программы.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Записывает свалку в файл.|

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Примечания
 Программа — это контейнер потоков, работающий в определенной архитектуре времени выполнения, в то время как процесс состоит из одной или нескольких программ.

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
