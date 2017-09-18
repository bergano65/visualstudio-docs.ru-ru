---
title: "EXCEPTION_STATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_STATE"
helpviewer_keywords: 
  - "Перечисление EXCEPTION_STATE"
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Указывает состояние исключения.  
  
## Синтаксис  
  
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
  
```c#  
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
  
## Члены  
 EXCEPTION\_NONE  
 Не остановится в исключении.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE  
 Остановите на срабатывание исключения.  , Описывающий событие исключения, этот пометить означает, что событие исключения событие о первичном исключении.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE  
 Остановить во втором включении исключения.  , Описывающий событие исключения, указывающее, что событие исключения событие исключения второй вероятность.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE  
 Сначала остановить срабатывание исключения в режиме пользователя.  , Описывающий событие исключения, указывающее, что событие исключения события режима пользователя о первой возможности захвата исключений.  
  
 EXCEPTION\_STOP\_USER\_UNCAUGHT  
 Остановите работу, когда исключение перехватывается в режиме пользователя.  , Описывающий событие исключения, указывающее, что событие исключения событие исключения в режиме пользователя uncaught.  
  
 EXCEPTION\_STOP\_ALL  
 Остановить на любом исключении.  Не используется, описывающее событие исключения.  
  
 \_BE\_CONTINUED НЕ EXCEPTION\_CAN  
 , Описывающий событие исключения, указывающее, что исключение не может продолжить.  
  
 EXCEPTION\_CODE\_SUPPORTED  
 Указывает, что исключение содержит код, поддерживающий их.  Используется при отображении исключения  
  
 EXCEPTION\_CODE\_DISPLAY\_IN\_HEX  
 Указывает, что код исключения должен отображаться в шестнадцатеричном формате.  Используется при отображении исключения.  
  
 EXCEPTION\_JUST\_MY\_CODE\_SUPPORTED  
 Указывает, что код исключения поддерживает JustMyCode.  Используется при отображении исключения.  
  
 EXCEPTION\_MANAGED\_DEBUG\_ASSISTANT  
 Указывает, что отладчик управляемого кода должен обрабатывать исключения.  Если отладчик не имеет значения по умолчанию обрабатывает исключения.  Эти данные передаются обработчику [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) метод и не используется в  [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) структура.  
  
 EXCEPTION\_STOP\_FIRST\_CHANCE\_USE\_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШИМ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION\_STOP\_SECOND\_CHANCE\_USE\_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШИМ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION\_STOP\_USER\_FIRST\_CHANCE\_USE\_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШИМ, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION\_STOP\_USER\_SECOND\_CHANCE\_USE\_PARENT  
 ЯВЛЯЕТСЯ УСТАРЕВШИМ, НЕ ИСПОЛЬЗУЙТЕ.  
  
## Заметки  
 Используется как `dwState` элемент  [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) структура для отображения состояния исключения и что можно сделать о них.  
  
 Эти значения также передаются [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) метод, чтобы установить состояние всех исключений.  
  
 Эти флаги могут объединяться с побитовый оператор ИЛИ.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)