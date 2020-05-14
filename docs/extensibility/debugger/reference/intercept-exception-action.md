---
title: INTERCEPT_EXCEPTION_ACTION Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc44a4fc5264566468777749d5732662ba81ed6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715070"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
Определяет, какие действия предпринимать при перехвате исключений.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

## <a name="parameters"></a>Параметры

`IEA_INTERCEPT`\
Позволяет перехватывать текущее исключение. Это единственное значение, поддерживаемое в настоящее время и должно быть указано.

## <a name="remarks"></a>Примечания
Эти значения передаются в метод [InterceptCurrentException.](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
