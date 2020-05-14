---
title: IDebugEngineProgram2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730296"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Этот интерфейс обеспечивает многопоточной поддержки отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка двигателя реализует этот интерфейс для поддержки одновременной отладки нескольких потоков. Этот интерфейс реализован на том же объекте, который реализует интерфейс [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface,](/cpp/atl/queryinterface) чтобы `IDebugProgram2` получить этот интерфейс из интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugEngineProgram2`.

|Метод|Описание|
|------------|-----------------|
|[Остановить](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Остановка всех потоков, работающих в этой программе.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Часы для выполнения (или прекратить наблюдение за выполнением) происходят на данном потоке.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Позволяет (или запрещает) оценку выражения происходит на данном потоке, даже если программа остановлена.|

## <a name="remarks"></a>Примечания
 Visual Studio называет этот интерфейс в ответ на событие [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) и установить "Смотреть на шаг потока" и "Смотреть для оценки экспрессии на поток" состояния программы. [Остановка](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) вызывается всякий раз, когда программа должна быть остановлена; этот метод дает программе возможность завершить все потоки.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
