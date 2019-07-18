---
title: IDebugProcess3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8db169a06864fad24ef7e6ce4c2d188e2a88ef1d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313844"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Этот интерфейс представляет выполняющемуся процессу и его программ. Этот интерфейс существует для замены нескольким методам в [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) интерфейс. Он позволяет контролировать все программы в процессе.

> [!NOTE]
> [По-прежнему](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), и [шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md) методы считаются устаревшими и больше не используется. Используйте соответствующие методы в `IDebugProcess3` интерфейса.

## <a name="syntax"></a>Синтаксис

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиком пользовательский порт, для управления программами как группу. Когда программ управляются как группу, можно управлять их выполнение и установить язык для вычислителя выражений. Этот интерфейс должен реализовываться поставщика порта.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс называется главным образом диспетчер отладки сеансов (SDM) для взаимодействия с группой программы, указанные в этом процессе.

 Вызовите [QueryInterface](/cpp/atl/queryinterface) на [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, наследуемых от [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Продолжает выполнение или пошагового выполнения процесса.|
|[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Начинает выполнение процесса.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Действия пересылать одну инструкцию или инструкции в процессе.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Возвращает причину, что процесс был запущен для отладки.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Задает язык, размещения, таким образом, чтобы модуль отладки можно загрузить средство оценки выражений, соответствующую.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Извлекает текущий язык для этого процесса.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Отключает Изменить и продолжить "(ENC) для этого процесса.<br /><br /> Пользовательский порт поставщик не реализует этот метод (всегда должны возвращать `E_NOTIMPL`).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Получение состояния ENC для этого процесса.<br /><br /> Пользовательский порт поставщик не реализует этот метод (всегда должны возвращать `E_NOTIMPL`).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Извлекает массив уникальных идентификаторов для доступных отладчиков.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)