---
title: ПАРСЕФЛАГС | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78890f088646842435198fa839c0f88cba5483b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880194"
---
# <a name="parseflags"></a>PARSEFLAGS
Указывает способ синтаксического анализа выражения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
typedef DWORD PARSEFLAGS;
```

```csharp
public enum enum_PARSEFLAGS { 
   PARSE_EXPRESSION            = 0x0001,
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000
};
```

## <a name="fields"></a>Поля
 `PARSE_EXPRESSION`\
 Указывает, что выражение не является оператором.

 `PARSE_FUNCTION_AS_ADDRESS`\
 Указывает, что выражение должно быть проанализировано (и понижено оценено) как адрес.

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 Указывает, что выражение анализируется во время разработки (то есть когда конструктор открыт).

## <a name="remarks"></a>Remarks
 Передается в качестве параметра методам [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
