---
title: DOCCONTEXT_COMPARE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737227"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Определяет критерии сравнения двух контекстов документов.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Поля
`DOCCONTEXT_EQUAL`\
Найдите первый контекст документа в списке, который равен контексту целевого документа.

`DOCCONTEXT_LESS_THAN`\
Найдите контекст первого документа в списке, который меньше контекста целевого документа.

`DOCCONTEXT_GREATER_THAN`\
Найдите контекст первого документа в списке, который больше контекста целевого документа.

`DOCCONTEXT_SAME_DOCUMENT`\
Найдите контекст первого документа в списке, который находится в том же документе, что и контекст целевого документа.

## <a name="remarks"></a>Примечания
Прошел в качестве аргумента методу [Сравнения.](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

Эти значения используются для определения критериев сравнения для поиска первого контекста документа в списке. Контексту документа предоставляется список контекстов документов `IDebugDocumentContext2::Compare` для сравнения с помощью метода. Первый контекст документа в списке, `true` для которого оператор сравнения затем возвращается.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Сравнить](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
