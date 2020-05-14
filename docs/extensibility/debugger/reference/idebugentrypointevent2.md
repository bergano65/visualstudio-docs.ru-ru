---
title: IDebugEntryPointEvent2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 531ff846f2488193ed7f3d9f200a1a4ea04df6f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730328"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Движок отладки (DE) отправляет этот интерфейс менеджеру отладки сеанса (SDM), когда программа собирается выполнить свою первую инструкцию пользовательского кода.

## <a name="syntax"></a>Синтаксис

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс как часть своей обычной работы. Интерфейс [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) должен быть реализован на том же объекте, что и этот интерфейс. SDM использует [QueryInterface](/cpp/atl/queryinterface) для `IDebugEvent2` доступа к интерфейсу.

## <a name="notes-for-callers"></a>Заметки для абонентов
 DE создает и отправляет объект события при загрузке отладки программы и готов выполнить первую инструкцию пользовательского кода. Событие отправляется с помощью функции обратного вызова [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) которая поставляется SDM при подключении к отладке программы.

## <a name="remarks"></a>Примечания
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) отправляется, когда программа собирается выполнить самую первую инструкцию. Например, `IDebugEntryPoint2` отправляется, когда программа собирается выполнить функцию `main` пользователя.

 Когда DE `IDebugEntryPointEvent2`отправляет, текущее положение кода должно быть при первой `main`инструкции пользовательского кода, как.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
