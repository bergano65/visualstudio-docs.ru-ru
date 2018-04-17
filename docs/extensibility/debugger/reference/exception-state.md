---
title: EXCEPTION_STATE | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1faa847d907af938bb5f91206a5f438bcba886a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
Указывает состояние исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Участники  
 EXCEPTION_NONE  
 Не останавливайте исключении.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Остановиться на первый вызов события исключения. При описании события исключения, этот флаг указывает, что события исключения является событие исключения первого шанса.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 На второй срабатывание исключения останавливается. При описании события исключения, указывает на событие исключения событий второй экземпляр исключения.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Остановиться на первой срабатывание исключения режима пользователя. При описании события исключения, указывает, что события исключения событий исключения первого шанса пользователя.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Остановитесь, когда режим пользователя исключение не обработано. При описании события исключения, указывает, что события исключения события исключения режима пользователя неперехваченных.  
  
 EXCEPTION_STOP_ALL  
 Остановите при любом исключении. Не используется при описании события исключения.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 При описании события исключения, указывает, что исключение не может быть продолжено из.  
  
 EXCEPTION_CODE_SUPPORTED  
 Указывает, что исключение имеет код его поддержки. Используемые при отображении исключения  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Указывает, что код исключения должен отображаться в шестнадцатеричном формате. Используется при отображении исключения.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Указывает, что код исключения поддерживает JustMyCode. Используется при отображении исключения.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Указывает, что отладчик управляемого кода обработки исключений. В противном случае набор по умолчанию отладчик обрабатывает исключения. Аргумент передается в [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) метода и не используется в [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШЕЙ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШЕЙ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШЕЙ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШЕЙ, НЕ ИСПОЛЬЗУЙТЕ.  
  
## <a name="remarks"></a>Примечания  
 Используется в качестве `dwState` членом [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры, в которых указывается состояние исключения и что можно сделать о нем.  
  
 Эти значения также передаются в [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) метод, чтобы установить для всех исключений.  
  
 Эти флаги могут объединяться с Побитовый оператор или.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)