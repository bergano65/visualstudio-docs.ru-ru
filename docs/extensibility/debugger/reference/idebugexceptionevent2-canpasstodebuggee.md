---
title: IDebugExceptionEvent2::CanPassToDebuggee | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c27ac3239fd6621a824f626a141a357241b03b1f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310578"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Определяет, поддерживает ли модуль отладки (DE) можно передать это исключение для отлаживаемой при возобновлении выполнения программы.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает один `S_OK` (исключение может передаваться в программу) или `S_FALSE` (исключение не может быть передано в).

## <a name="remarks"></a>Примечания
 DE должен иметь действие по умолчанию для передачи для отлаживаемой программы. Интегрированная среда разработки может появиться [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) событий и вызовов [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md) метод без вызова `CanPassToDebuggee` метод. Таким образом DE должны иметь варианта по умолчанию для передачи в исключение, или нет.

## <a name="see-also"></a>См. также
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)