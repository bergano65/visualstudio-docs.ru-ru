---
title: CONSTRUCTOR_ENUM Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f9e123399ed2378eaf63944f9a1527ef024c0cd6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737624"
---
# <a name="constructor_enum"></a>CONSTRUCTOR_ENUM
Выбирает различные типы конструкторов.

## <a name="syntax"></a>Синтаксис

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="fields"></a>Поля
`crAll`\
Выбирает всех конструкторов.

`crNonStatic`\
Выбирает нестатических конструкторов.

`crStatic`\
Выбирает статические конструкторы.

## <a name="remarks"></a>Примечания
Прошел в качестве аргумента методу [EnumConstructors.](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)

## <a name="requirements"></a>Требования
Заголовок: sh.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
