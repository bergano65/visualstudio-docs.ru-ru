---
title: EVALFLAGS90 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 80f281e65d4dd7b2df24233552bdc46d4b29bebe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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