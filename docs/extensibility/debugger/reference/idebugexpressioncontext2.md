---
title: IDebugExpressionКонтекст2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729640"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Этот интерфейс представляет собой контекст для оценки выражения

## <a name="syntax"></a>Синтаксис

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представлять контекст, в котором можно оценить выражение.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Звонок [в GetExpressionExpression](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает этот интерфейс. Этот интерфейс доступен только тогда, когда отладка программы была приостановлена и доступна рамка стека.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugExpressionContext2`.

|Метод|Описание|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Извлекает название контекста оценки.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Сравнивает текстовое выражение для оценки.|

## <a name="remarks"></a>Примечания
 Контекст оценки можно рассматривать как область для выполнения оценки выражения.

 Когда программа остановлена, диспетчер отладки сеанса (SDM) получает кадр стека из DE с вызовом на [EnumFrameInfo.](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) Затем SDM вызывает [GetExpressionContext,](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) чтобы получить `IDebugExpressionContext2` интерфейс. За этим следует звонок [в ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания интерфейса [IDebugExpression2,](../../../extensibility/debugger/reference/idebugexpression2.md) который представляет собой готовое к оценке выражение, готовое к оценке.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
