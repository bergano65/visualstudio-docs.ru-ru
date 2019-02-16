---
title: BP_COND_STYLE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8ca4f551f4dd6541bad9d73b5e91c671ad80492
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318307"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Указывает стиль условие точки останова для ожидающих и привязан точки останова.

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

## <a name="members"></a>Участники
BP_COND_NONE  
Точка останова срабатывает в том случае, когда достигается положение точки останова. Не указано условие точки останова.

BP_COND_WHEN_TRUE  
Срабатывает точка останова, только если условное выражение, связанные с точкой останова принимает значение `true`.

BP_COND_WHEN_CHANGED  
Срабатывает точка останова только в том случае, если значение условного выражения, связанное с точкой останова отличается от его предыдущей оценки.

## <a name="remarks"></a>Примечания
Используется для `styleCondition` членом [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структуры.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
[Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
