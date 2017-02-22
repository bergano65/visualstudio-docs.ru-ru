---
title: "EVALFLAGS90 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Перечисление EVALFLAGS90"
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# EVALFLAGS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Перечисляет допустимые значения для флагов, отслеживающие оценки выражений.  Это перечисление расширяет [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисление.  
  
## Синтаксис  
  
```cpp#  
enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
typedef DWORD EVALFLAGS90;  
```  
  
```c#  
public enum enum_EVALFLAGS90  
{  
   // VS 8.0 values  
   EVAL90_RETURNVALUE                 = 0x0002,  
   EVAL90_NOSIDEEFFECTS               = 0x0004,  
   EVAL90_ALLOWBPS                    = 0x0008,  
   EVAL90_ALLOWERRORREPORT            = 0x0010,  
   EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,  
   EVAL90_NOFUNCEVAL                  = 0x0080,  
   EVAL90_NOEVENTS                    = 0x1000,  
   EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,  
   EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,  
  
   // Values added in VS 9.0  
   EVAL90_FORCE_EVALUATION_NOW        = 0x8000  
};  
```  
  
#### Параметры  
 EVAL90\_RETURNVALUE  
 Указывает, что было вычислено возвращаемое значение, если они есть.  
  
 EVAL90\_NOSIDEEFFECTS  
 Указывает, что побочные эффекты, предоставляемых.  
  
 EVAL90\_ALLOWBPS  
 Определяет остановки в точках останова.  
  
 EVAL90\_ALLOWERRORREPORT  
 Указывает, что отчеты об ошибках на узле, который требуется разрешить.  В основном используется для оценки выражений в скрипте в Internet Explorer.  
  
 EVAL90\_FUNCTION\_AS\_ADDRESS  
 Обеспечивает функции должен вычисляться как адреса, вместо вызова функции.  
  
 EVAL90\_NOFUNCEVAL  
 Предотвращает функцию из быть вычисляемым.  Например, рассмотрим `int` токен в выражении  `myExpression(int) + 10`.  Эта функция может правильно вычислить в качестве адреса, но не в качестве значения.  
  
 EVAL90\_NOEVENTS  
 Пометить для указания того, что события, происходящие во время оценки выражений не должны быть отправлены к сеансу отладки \(SDM\) или диспетчер в интегрированной среде разработки.  
  
 EVAL90\_DESIGN\_TIME\_EXPR\_EVAL  
 Включает вычисление выражений в процессе разработки.  
  
 EVAL90\_ALLOW\_IMPLICIT\_VARS  
 Обеспечивает неявное создание переменной.  
  
 EVAL90\_FORCE\_EVALUATION\_NOW  
 Принудительное вычисление немедленное.  Это полезно обслуживание запроса, например запрос пользователя.  
  
## Требования  
 Заголовок: Msdbg90.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)