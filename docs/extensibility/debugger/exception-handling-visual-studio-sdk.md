---
title: "Исключение при обработке (SDK для Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [пакет SDK для отладки], обработка исключений"
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Исключение при обработке (SDK для Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс, который происходит, когда исключения возникают.  
  
## Процесс обработки ошибок  
  
1.  Если исключение сначала создается, но до обработки обработчиком исключений в отлаживаемом программе, отладчик \(DE\) отправляет IDebugExceptionEvent2 к сеансу отладки \(SDM\) как диспетчер остановки событие.  `IDebugExceptionEvent2` отправляет если только параметры для исключения \(заданного в диалоговом окне исключения в пакете отладки\) определяют, что пользователь хочет остановить на уведомления о первой возможности захвата исключений.  
  
2.  Вызовы SDM [IDebugExceptionEvent2:: GetException](../Topic/IDebugExceptionEvent2::GetException.md) получить свойство исключения.  
  
3.  Вызовы пакета отладки [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) указать, какие параметры представления пользователю.  
  
4.  Пакет отладки запрашивает пользователя, как обрабатывать исключения, открыв диалоговое окно о первичном исключении.  
  
5.  Если пользователь выбирает, чтобы продолжить, то вызовы SDM [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Если метод возвращает значение S\_OK, то вызовы [IDebugExceptionEvent2:: PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         \-или\-  
  
         Если метод возвращает значение S\_FALSE, ему присваивается отлаживаемой программы второй возможность обработки исключения.  
  
6.  Если отлаживаемой программы отсутствует обработчик исключения второй вероятность, DE отправляет `IDebugExceptionEvent2` SDM, как к  **EVENT\_SYNC\_STOP**.  
  
7.  Пакет отладки запрашивает пользователя, как обрабатывать исключения, открыв диалоговое окно о первичном исключении.  
  
8.  Вызовы пакета отладки [IDebugExceptionEvent2:: CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) указать, какие параметры представления пользователю.  
  
9. Пакет отладки запрашивает пользователя, как обрабатывать исключения, открыв диалоговое окно исключения второй вероятность.  
  
10. Если метод возвращает значение S\_OK, то вызовы `IDebugExceptionEvent2::PassToDebuggee`.  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)