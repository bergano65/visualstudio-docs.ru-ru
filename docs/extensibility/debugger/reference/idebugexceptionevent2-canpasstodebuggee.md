---
title: IDebugExceptionEventevent2::CanPassToDebuggee Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729866"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Определяет, поддерживает ли отладка двигателя (DE) возможность передачи этого исключения в программу, которая отлажется при возобновлении выполнения.

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
 Возвращает `S_OK` либо (исключение может быть передано `S_FALSE` в программу) или (исключение не может быть передано).

## <a name="remarks"></a>Примечания
 DE должен иметь действие по умолчанию для передачи в отладку. IDE может получить событие [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) и вызвать `CanPassToDebuggee` метод [«Продолжить»,](../../../extensibility/debugger/reference/idebugprocess3-continue.md) не вызывая метод. Таким образом, DE должен иметь случай по умолчанию для передачи исключения или нет.

## <a name="see-also"></a>См. также
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
