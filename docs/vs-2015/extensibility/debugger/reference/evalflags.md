---
title: EVALFLAGS | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51ac8f5ae6ed64c9b5a2d6eaae1ac5062840d42d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811416"
---
# <a name="evalflags"></a>EVALFLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает флаги, определяющие вычисления выражения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
## <a name="members"></a>Участники  
 EVAL_RETURNVALUE  
 Указывает, что возвращаемое значение, если таковое имеется, вычисляется.  
  
 EVAL_NOSIDEEFFECTS  
 Указывает, что побочные эффекты не разрешается.  
  
 EVAL_ALLOWBPS  
 Указывает остановки точек останова.  
  
 EVAL_ALLOWERRORREPORT  
 Указывает отчетов к узлу разрешен об ошибках. В основном используется для вычисления выражений в скрипте в Internet Explorer.  
  
 EVAL_FUNCTION_AS_ADDRESS  
 Функции силы для оценки в качестве адреса, вместо вызова функции.  
  
 EVAL_NOFUNCEVAL  
 Запрещает вычисляется функция. Например, рассмотрим `int` маркера в выражении `myExpression(int) + 10`. Эта функция может вычисляться правильно, как адрес, а не как значение.  
  
 EVAL_NOEVENTS  
 Флаг, указывающий, что события, происходящие во время вычисления выражения не следует отправлять в диспетчер отладки сеансов (SDM) или в интегрированную среду разработки.  
  
## <a name="remarks"></a>Примечания  
 Эти флаги передаются в качестве аргумента [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) и [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) методы.  
  
 Эти флаги могут быть объединены с помощью побитового логического Сложения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)

