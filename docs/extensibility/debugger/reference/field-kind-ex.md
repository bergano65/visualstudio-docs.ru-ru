---
title: FIELD_KIND_EX | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd481883c826ff21a82b52bdd82de087b6219b58
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309019"
---
# <a name="fieldkindex"></a>FIELD_KIND_EX
Перечисляет дополнительные типы полей, [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) может содержаться в объекте. Это перечисление расширяет [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) перечисления.

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
Поле содержит переменную в метод.

`FIELD_TYPE_EX_CLASSVAR`\
Поле содержит переменной класса.

## <a name="requirements"></a>Требования
Заголовок: Sh.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
