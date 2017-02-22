---
title: "EVALFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVALFLAGS"
helpviewer_keywords: 
  - "Перечисление EVALFLAGS"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает флаги, которые контролируют оценки выражений.  
  
## Синтаксис  
  
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
  
```c#  
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
  
## Члены  
 EVAL\_RETURNVALUE  
 Указывает, что было вычислено возвращаемое значение, если они есть.  
  
 EVAL\_NOSIDEEFFECTS  
 Указывает, что побочные эффекты, предоставляемых.  
  
 EVAL\_ALLOWBPS  
 Определяет остановки в точках останова.  
  
 EVAL\_ALLOWERRORREPORT  
 Определяет отчеты об ошибках на узле, который требуется разрешить.  В основном используется для оценки выражений в скрипте в Internet Explorer.  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 Обеспечивает функции должен вычисляться как адреса, вместо вызова функции.  
  
 EVAL\_NOFUNCEVAL  
 Предотвращает функцию из быть вычисляемым.  Например, рассмотрим `int` токен в выражении  `myExpression(int) + 10`.  Эта функция может правильно вычислить в качестве адреса, но не в качестве значения.  
  
 EVAL\_NOEVENTS  
 Пометить для указания того, что события, происходящие во время оценки выражений не должны быть отправлены к сеансу отладки \(SDM\) или диспетчер в интегрированной среде разработки.  
  
## Заметки  
 Эти флаги передаются в качестве аргумента [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) и  [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) методы.  
  
 Эти флаги могут объединяться с побитовый оператор ИЛИ.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)