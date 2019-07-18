---
title: IDebugExceptionEvent2::PassToDebuggee | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca6c35b3d4a238404b92b50de486a7671bfc4726
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326100"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Определяет исключение должно передаваться программу, отлаживаемую при возобновлении выполнения программы, или если исключение должно быть удалено.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>Параметры
`fPass`\
[in] Ненулевое значение (`TRUE`) Если исключение должно передаваться программу, отлаживаемую при возобновлении выполнения программы, или нуль (`FALSE`) Если исключение должно быть удалено.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызов этого метода не вызывает фактически любой код, выполняемый в отлаживаемой программы. Вызов является просто установить состояние следующего выполнения кода. Например, вызовы [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) метод может вернуть `S_OK` с [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` поле "значение" `EXCEPTION_STOP_SECOND_CHANCE`.

 Интегрированная среда разработки может появиться [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событий и вызовов [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md) метод. Модуль отладки (DE) должны иметь поведение по умолчанию для обработки в том случае, если `PassToDebuggee` метод не вызывается.

## <a name="see-also"></a>См. также
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)