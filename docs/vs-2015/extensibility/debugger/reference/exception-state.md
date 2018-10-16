---
title: EXCEPTION_STATE | Документация Майкрософт
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
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c35c59d491f28051bf7b5149ddcff74a386d179e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306771"
---
# <a name="exceptionstate"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает состояние исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Не останавливайте на исключении.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Останавливается на первой обработки исключения. При описании события исключения, этот флаг указывает, что исключение это событие исключения первого шанса.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 На второй срабатывание исключения останавливается. При описании события исключения, указывает, что события исключения является событие второй возможности захвата исключений.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Останавливается на первой обработки исключения режима пользователя. При описании события исключения, указывает, что события исключения является событием исключения первого шанса пользователя.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Остановитесь, когда не перехватывается исключение режима пользователя. При описании события исключения, указывает, что события исключения является событие исключения режима пользователя неперехваченных.  
  
 EXCEPTION_STOP_ALL  
 Остановите по любому исключению. Не используется при описании события исключения.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 При описании события исключения, указывает, что исключение не может быть продолжено из.  
  
 EXCEPTION_CODE_SUPPORTED  
 Указывает, что исключение имеет код, который поддерживает его. Используемые при отображении исключения  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Указывает, что код исключения должно отображаться в шестнадцатеричном формате. Для отображения исключение.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Указывает, что код исключения поддерживает JustMyCode. Для отображения исключение.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Указывает, что отладчик управляемого кода должен обрабатывать исключения. В противном случае набор, по умолчанию отладчик обрабатывает исключения. Эти данные передаются [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) метода и не используется в [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры.  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 УСТАРЕВШИЕ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 УСТАРЕВШИЕ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 УСТАРЕВШИЕ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 УСТАРЕВШИЕ, НЕ ИСПОЛЬЗУЙТЕ.  
  
## <a name="remarks"></a>Примечания  
 Используется в качестве `dwState` членом [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структуры, в которых указывается состояние исключения и что можно сделать о нем.  
  
 Эти значения также передаются [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) метод для задания состояния всех исключений.  
  
 Эти флаги могут быть объединены с помощью побитового логического Сложения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)

