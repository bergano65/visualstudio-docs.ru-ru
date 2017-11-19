---
title: "EVALFLAGS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EVALFLAGS
helpviewer_keywords: EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45bef946605818f11d0199600849fd49b5463ab8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="evalflags"></a>EVALFLAGS
Указывает флаги, управляющие вычисления выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Члены  
 EVAL_RETURNVALUE  
 Указывает, вычисления и возвращаемое значение, если таковая имеется.  
  
 EVAL_NOSIDEEFFECTS  
 Указывает, не допускается побочные эффекты.  
  
 EVAL_ALLOWBPS  
 Указывает остановки точек останова.  
  
 EVAL_ALLOWERRORREPORT  
 Указывает отчетов для узла разрешаются. В основном используется для вычисления выражений в скрипте в Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Принудительно вызывает функции для оценки в качестве адреса, вместо вызова функции.  
  
 EVAL_NOFUNCEVAL  
 Препятствует при вычислении функции. Например, рассмотрим `int` маркера в выражении `myExpression(int) + 10`. Эта функция может вычисляться неправильно, адрес, а не значение.  
  
 EVAL_NOEVENTS  
 Флаг, указывающий, не отправляются события, происходящие во время вычисления выражения для диспетчера сеанса отладки (SDM) или в интегрированную среду разработки.  
  
## <a name="remarks"></a>Примечания  
 Эти флаги передаются в качестве аргумента для [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) и [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) методы.  
  
 Эти флаги могут объединяться с Побитовый оператор или.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)