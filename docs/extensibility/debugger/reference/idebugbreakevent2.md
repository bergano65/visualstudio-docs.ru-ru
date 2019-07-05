---
title: IDebugBreakEvent2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c500c6a54cc63dbcb8c7c6ad23c92d2105b9842
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314405"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Этот интерфейс указывает диспетчер отладки сеансов (SDM), что асинхронные прерывания успешно завершена.

## <a name="syntax"></a>Синтаксис

```
IDebugBreakEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 DE реализует этот интерфейс для поддержки пользователя разрывы в программе. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) на один и тот же объект как этот интерфейс должен быть реализован интерфейс (использует SDM [QueryInterface](/cpp/atl/queryinterface) для доступа к `IDebugEvent2` интерфейс).

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовы SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) когда пользователь запросил будут приостановлены отлаживаемой программы. Когда программа успешно приостановлен, DE отправляет `IDebugBreakEvent2` событий. Это событие отправляется с помощью [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) функции обратного вызова, предоставляемой SDM, если он присоединен к отлаживаемой программы.

## <a name="remarks"></a>Примечания
 Например, пользователь может выбрать **прервать все** команды **Отладка** меню для выхода из программы, на котором выполняется бесконечный цикл. SDM сообщает программе, чтобы остановить путем вызова [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Отправляет DE `IDebugBreakEvent2` наконец остановки программы.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)