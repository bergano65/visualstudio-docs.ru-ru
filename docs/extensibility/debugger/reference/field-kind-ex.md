---
title: FIELD_KIND_EX Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0c13d83f80b311838eca32945462c1f17ca23f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736875"
---
# <a name="field_kind_ex"></a>FIELD_KIND_EX
Перечисляет дополнительные виды полей, которые может содержать объект [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Этот пересчет расширяет [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) перечисление.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
typedef DWORD FIELD_KIND_EX;
```

```csharp
public enum enum_FIELD_KIND_EX
{
    FIELD_KIND_EX_NONE = 0,
    FIELD_TYPE_EX_METHODVAR = 0x1,
    FIELD_TYPE_EX_CLASSVAR = 0x2
};
```

## <a name="fields"></a>Поля
`FIELD_KIND_EX_NONE`\
Поле не содержит расширенного типа.

`FIELD_TYPE_EX_METHODVAR`\
Поле содержит переменную метода.

`FIELD_TYPE_EX_CLASSVAR`\
Поле содержит переменную класса.

## <a name="requirements"></a>Требования
Заголовок: Sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
