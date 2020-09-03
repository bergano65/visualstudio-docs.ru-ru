---
title: BP_COND_STYLE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738112"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Задает стиль условия точки останова для ожидающих и связанных точек останова.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Поля
`BP_COND_NONE`\
Вызывает точку останова, когда достигнута точка точки останова. Условие для точки останова не указано.

`BP_COND_WHEN_TRUE`\
Вызывает точку останова только в том случае, если условное выражение, связанное с точкой останова, имеет значение `true` .

`BP_COND_WHEN_CHANGED`\
Вызывает точку останова только в том случае, если значение условного выражения, связанное с точкой останова, изменилось по сравнению с предыдущим вычислением.

## <a name="remarks"></a>Remarks
Используется для `styleCondition` элемента структуры [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
