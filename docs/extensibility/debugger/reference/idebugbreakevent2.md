---
title: IDebugBreakEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1af6ce13de529fef5e16b3bc1be7053f0e1347b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735403"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Этот интерфейс сообщает менеджеру отладки сеанса (SDM), что асинхронный перерыв был успешно завершен.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс для поддержки пользовательских перерывов в программе. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот `IDebugEvent2` интерфейс (SDM использует [queryInterface](/cpp/atl/queryinterface) для доступа к интерфейсу).

## <a name="notes-for-callers"></a>Заметки для абонентов
 SDM вызывает [CauseBreak,](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) когда пользователь запросил отладку программы для приостановки. Когда программа успешно приостановлена, DE отправляет `IDebugBreakEvent2` событие. Это событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) поставляемой SDM при его подключении к отладке программы.

## <a name="remarks"></a>Примечания
 Например, пользователь может выбрать команду **Break All** в меню **Debug,** чтобы выйти из программы, которая работает бесконечный цикл. SDM говорит программе, чтобы остановить, позвонив [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). DE отправляет, `IDebugBreakEvent2` когда программа, наконец, останавливается.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
