---
title: ЕВАЛФЛАГС | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9e6ee00402c13b2a79e4e6757a127211eda9c3c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149384"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает флаги, управляющие вычислением выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_EVALFLAGS {  
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
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>Участники  
 EVAL_RETURNVALUE  
 Указывает, что должно быть вычислено возвращаемое значение, если оно имеется.  
  
 EVAL_NOSIDEEFFECTS  
 Указывает, что побочные эффекты не допускаются.  
  
 EVAL_ALLOWBPS  
 Задает остановку в точках останова.  
  
 EVAL_ALLOWERRORREPORT  
 Указывает, что сообщение об ошибках должно быть разрешено узлу. В основном используется для вычисления выражений в скрипте в Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Заставляет функции оцениваться как адреса, а не вызывать функцию.  
  
 EVAL_NOFUNCEVAL  
 Предотвращает вычисление функции. Например, рассмотрим `int` маркер в выражении `myExpression(int) + 10` . Эта функция может быть правильно оценена как адрес, но не как значение.  
  
 EVAL_NOEVENTS  
 Флаг, указывающий, что события, происходящие во время оценки выражения, не должны отправляться в Диспетчер отладки сеанса (SDM) или в интегрированную среду разработки.  
  
## <a name="remarks"></a>Remarks  
 Эти флаги передаются в качестве аргумента методам [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) и [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) .  
  
 Эти флаги можно сочетать с помощью побитового или.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
