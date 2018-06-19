---
title: EVALFLAGS90 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 120bf38afbf05f367757de3a5e453cab8b4311b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102711"
---
# <a name="evalflags90"></a>EVALFLAGS90
Перечисляет допустимые значения для флаги, управляющие вычисления выражения. Это перечисление расширяет [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>Параметры  
 EVAL90_RETURNVALUE  
 Указывает, вычисления и возвращаемое значение, если таковая имеется.  
  
 EVAL90_NOSIDEEFFECTS  
 Указывает, не допускается побочные эффекты.  
  
 EVAL90_ALLOWBPS  
 Указывает остановки точек останова.  
  
 EVAL90_ALLOWERRORREPORT  
 Указывает ошибку отчетов к узлу разрешаются. В основном используется для вычисления выражений в скрипте в Internet Explorer.  
  
 EVAL90_FUNCTION_AS_ADDRESS  
 Принудительно вызывает функции для оценки в качестве адреса, вместо вызова функции.  
  
 EVAL90_NOFUNCEVAL  
 Препятствует при вычислении функции. Например, рассмотрим `int` маркера в выражении `myExpression(int) + 10`. Эта функция может вычисляться неправильно, адрес, а не значение.  
  
 EVAL90_NOEVENTS  
 Флаг, указывающий, не отправляются события, происходящие во время вычисления выражения для диспетчера сеанса отладки (SDM) или в интегрированную среду разработки.  
  
 EVAL90_DESIGN_TIME_EXPR_EVAL  
 Позволяет вычисление выражений во время разработки.  
  
 EVAL90_ALLOW_IMPLICIT_VARS  
 Позволяет неявного создания переменной.  
  
 EVAL90_FORCE_EVALUATION_NOW  
 Принудительное вычисление немедленное. Это полезно при обслуживании запроса, например запрос пользователя.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg90.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)