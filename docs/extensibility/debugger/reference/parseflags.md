---
title: ПАРСЕХЕСИ Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714122"
---
# <a name="parseflags"></a>PARSEFLAGS
Определяет, как разобрать выражение.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Поля
 `PARSE_EXPRESSION`\
 Означает, что выражение не является заявлением.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Означает, что выражение должно быть разобрано (а затем оценено) в качестве адреса.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Означает, что выражение разбирается во время проектирования (т.е. при открытии конструктора).

## <a name="remarks"></a>Примечания
 Прошел в качестве параметра к методам [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и [Parse.](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Синтаксический анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
