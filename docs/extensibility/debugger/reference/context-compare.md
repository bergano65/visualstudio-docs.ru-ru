---
title: CONTEXT_COMPARE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737602"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Определяет критерии сравнения двух контекстов памяти.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Поля
`CONTEXT_EQUAL`\
Найдите первый контекст памяти в списке, который равен целевому контексту памяти.

`CONTEXT_LESS_THAN`\
Найдите первый контекст памяти в списке, который меньше, чем целевой контекст памяти.

`CONTEXT_GREATER_THAN`\
Найдите первый контекст памяти в списке, который больше, чем целевой контекст памяти.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Найдите первый контекст памяти в списке, который меньше или равен целевому контексту памяти.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Найдите первый контекст памяти в списке, который больше или равен целевому контексту памяти.

`CONTEXT_SAME_SCOPE`\
Найдите первый контекст памяти в списке, который находится в той же области, что и контекст целевой памяти.

`CONTEXT_SAME_FUNCTION`\
Найдите первый контекст памяти в списке, который находится в той же функции, что и область целевой памяти.

`CONTEXT_SAME_MODULE`\
Найдите первый контекст памяти в списке, который находится в том же модуле, что и контекст целевой памяти.

`CONTEXT_SAME_PROCESS`\
Найдите первый контекст памяти в списке, который находится в том же процессе, что и контекст целевой памяти.

## <a name="remarks"></a>Примечания
Прошел в качестве аргумента методу [Сравнения.](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)

Эти значения используются для поиска первого контекста памяти в списке, который удовлетворяет указанным критериям сравнения. Контексту памяти дается список контекстов памяти `IDebugMemoryContext2::Compare` для сравнения с помощью метода. Первый контекст памяти в списке, `true` для которого оператор сравнения затем возвращается.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Сравнить](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
