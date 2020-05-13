---
title: СТЕПКИНД Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ed2877c880d3cd2674f62b4f900a6e923bb29d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713559"
---
# <a name="stepkind"></a>STEPKIND
Определяет вид шага для шага.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
typedef DWORD STEPKIND;
```

```csharp
public enum enum_STEPKIND { 
   STEP_INTO      = 0,
   STEP_OVER      = 1,
   STEP_OUT       = 2,
   STEP_BACKWARDS = 3
};
```

## <a name="fields"></a>Поля
 `STEP_INTO`\
 Шаги в функцию.

 `STEP_OVER`\
 Шаги над функцией.

 `STEP_OUT`\
 Выйти из функции.

 `STEP_BACKWARDS`\
 Шаги назад в функцию.

## <a name="remarks"></a>Примечания
 Прошел в качестве аргумента методу [Step.](../../../extensibility/debugger/reference/idebugprocess3-step.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md)
