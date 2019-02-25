---
title: PARSEFLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56ba1933d1b63f9af863b115972f3ecf1dfc4346
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695717"
---
# <a name="parseflags"></a>PARSEFLAGS
Указывает, как выполнить синтаксический анализ выражения.

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

## <a name="members"></a>Участники
 PARSE_EXPRESSION указывает, что выражение не является оператором.

 PARSE_FUNCTION_AS_ADDRESS указывает, что выражение является для синтаксического анализа (и более поздней версии вычисляется) как адрес.

 PARSE_DESIGN_TIME_EXPR_EVAL указывает, что выражение анализируется во время разработки (то есть, когда конструктор открыт).

## <a name="remarks"></a>Примечания
 Переданный в качестве параметра для [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и [проанализировать](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) методы.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)