---
title: ИдебугКериИнженер2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b1784055c54c9243237c81edb708e13de9bc5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720649"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Этот интерфейс позволяет диспетчеру отладки сеанса (SDM) получить интерфейс, представляющий движок отладки (DE).

## <a name="syntax"></a>Синтаксис

```
IDebugQueryEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс на объектах, которые реализуют наиболее распространенные интерфейсы DE (например, [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)и [IDebugStackFrame2),](../../../extensibility/debugger/reference/idebugstackframe2.md)чтобы обеспечить доступ к интерфейсу [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) самого DE.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [queryInterface](/cpp/atl/queryinterface) на типичный интерфейс DE, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugQueryEngine2`.

|Метод|Описание|
|------------|-----------------|
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Получает пользовательский интерфейс отладки двигателя (DE).|

## <a name="remarks"></a>Примечания
 Этот интерфейс обычно реализуется в объекте, который реализует интерфейс [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) для поддержки заказанных причинно-следственных связей, выполняя функции; то есть, когда отладчик выходит из функции, следующая функция для выполнения может быть не предыдущей функцией в стеке, но функция в другом потоке вообще. Для определения "причинность", [см.](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
