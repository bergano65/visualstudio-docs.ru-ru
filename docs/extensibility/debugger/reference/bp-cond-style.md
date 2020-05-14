---
title: BP_COND_STYLE Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738112"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Определяет стиль состояния точки разрыва для ожидающих и связанных моментов.

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
Запускает точку разрыва при достигепозиции точки разрыва. Условие точки разрыва не указано.

`BP_COND_WHEN_TRUE`\
Запускает точку разрыва только тогда, когда условное `true`выражение, связанное с точкой разрыва, оценивается до .

`BP_COND_WHEN_CHANGED`\
Запускает точку разрыва только тогда, когда значение условного выражения, связанного с точкой разрыва, изменилось по сравнению с предыдущей оценкой.

## <a name="remarks"></a>Примечания
Используется для `styleCondition` члена [структуры BP_CONDITION.](../../../extensibility/debugger/reference/bp-condition.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
