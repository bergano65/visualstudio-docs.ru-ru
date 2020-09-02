---
title: ПАРСЕФЛАГС | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a9ebe244f3e1c1f3f95508d6df979edee2d4aed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205120"
---
# <a name="parseflags"></a>PARSEFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает способ синтаксического анализа выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 PARSE_EXPRESSION  
 Указывает, что выражение не является оператором.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Указывает, что выражение должно быть проанализировано (и понижено оценено) как адрес.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Указывает, что выражение анализируется во время разработки (то есть когда конструктор открыт).  
  
## <a name="remarks"></a>Remarks  
 Передается в качестве параметра методам [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [парсетекст](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
