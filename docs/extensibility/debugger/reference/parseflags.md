---
title: "PARSEFLAGS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PARSEFLAGS
helpviewer_keywords: PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ae1237efe578bdd51c6ed148a1dab7a7617fee30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="parseflags"></a>PARSEFLAGS
Указывает, как выполнить синтаксический анализ выражения.  
  
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
  
## <a name="members"></a>Участники  
 PARSE_EXPRESSION  
 Указывает, что выражение не является инструкцией.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Указывает, что выражение для синтаксического анализа (и более поздней версии вычисляется) как адрес.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Указывает что выражение анализируется во время разработки (то есть, когда конструктор открыт).  
  
## <a name="remarks"></a>Примечания  
 Переданное в качестве параметра для [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) и [проанализировать](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) методы.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Анализ](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)