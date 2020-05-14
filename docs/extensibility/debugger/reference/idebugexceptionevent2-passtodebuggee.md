---
title: IDebugExceptionEventEvent2::PassToDebuggee Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aec6f460295b59b2b5455b83d5b0be554bca24fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729835"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
Уточняется, следует ли передавать исключение программе, которая отлажается при возобновлении выполнения, или следует отказаться от этого исключения.

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
(в) Nonzero`TRUE`( ), если исключение должно быть передано программе, которая отлажается при возобновлении выполнения, или ноль (),`FALSE`если исключение должно быть отброшено.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Вызов этого метода на самом деле не приводит к тому, что в отладке программы не будет выполняться какой-либо код. Вызов заключается лишь в установлении состояния для следующего выполнения кода. Например, вызовы на метод [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) могут возвращаться `S_OK` с [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md).`dwState` поле установлено для `EXCEPTION_STOP_SECOND_CHANCE`.

 IDE может получить событие [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) и вызвать метод [Продолжения.](../../../extensibility/debugger/reference/idebugprogram2-continue.md) Двигатель отладки (DE) должен иметь поведение по `PassToDebuggee` умолчанию для обработки дела, если метод не вызывается.

## <a name="see-also"></a>См. также
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
