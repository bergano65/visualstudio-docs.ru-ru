---
title: IDebugПроцесс3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723543"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Этот интерфейс представляет собой запущенный процесс и его программы. Этот интерфейс существует в качестве замены нескольким методам в интерфейсе [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Он обеспечивает контроль над всеми программами в этом процессе.

> [!NOTE]
> [Продолжить,](../../../extensibility/debugger/reference/idebugprogram2-continue.md) [выполнить,](../../../extensibility/debugger/reference/idebugprogram2-execute.md)и [шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md) методы унижаются и больше не должны использоваться. Вместо этого используйте `IDebugProcess3` соответствующие методы на интерфейсе.

## <a name="syntax"></a>Синтаксис

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован поставщиком пользовательских портов для управления программами как группы. Когда программы управляются как группа, вы можете контролировать их выполнение и установить язык для оценщика выражения. Этот интерфейс должен быть реализован поставщиком порта.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс вызывается в первую очередь менеджером отладки сеанса (SDM) для взаимодействия с группой программ, определенных в этом процессе.

 Для получения этого интерфейса позвоните [в queryInterface](/cpp/atl/queryinterface) на [интерфейсе IDebugProcess2.](../../../extensibility/debugger/reference/idebugprocess2.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованных `IDebugProcess3` от [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md)реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Продолжает выполнение или прохождение процесса.|
|[Выполнить](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Начинается выполнение процесса.|
|[Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Шаги вперед одну инструкцию или заявление в процессе.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Получает причину, по которой процесс был запущен для отладки.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Устанавливает язык хостинга таким образом, чтобы отладка двигателя может загрузить соответствующий оценщик выражения.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Извлекает язык, установленный в настоящее время для этого процесса.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Отстраняет от сотворечки для этого процесса.<br /><br /> Поставщик пользовательских портов не реализует этот метод `E_NOTIMPL`(он всегда должен вернуться).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Получите состояние ENC для этого процесса.<br /><br /> Поставщик пользовательских портов не реализует этот метод `E_NOTIMPL`(он всегда должен вернуться).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Извлекает массив уникальных идентификаторов для доступных двигателей отладки.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
