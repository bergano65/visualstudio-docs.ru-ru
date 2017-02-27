---
title: "IDebugExceptionEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExceptionEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugExceptionEvent2"
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExceptionEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Отладчик \(DE\) отправляет этот интерфейс для сеанса отладки \(SDM\) диспетчер при возникновении исключения в настоящий момент, выполнить программу.  
  
## Синтаксис  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, чтобы сообщить о появлении исключения в отлаживаемом программе.   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события для оповещения исключение.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложило в отлаживаемом программе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IDebugExceptionEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetException](../Topic/IDebugExceptionEvent2::GetException.md)|Возвращает подробные сведения об исключении, которое сгорело это событие.|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Получает понятное описание создание исключения, сгорело это событие.|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Определяет, поддерживает ли отладчик \(DE\) параметр передача это исключение в отлаживанными программе, когда выполнение продолжится.|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Определяет, должно ли исключение передается в отлаживаемом программе, когда выполнение возобновлении или если исключение должно отменено.|  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Заметки  
 Прежде чем отправлять событие, DE проверяется, является ли это событие исключения было показано исключение перв\-шансом или второй вероятность предыдущим вызовом метода [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md).  Если он был подписан с исключением, то о первичном `IDebugExceptionEvent2` событие отправляется SDM.  Если нет, DE дает приложению возможность обработки исключения.  Если обработчик исключений не предоставлен, и если исключение было показано, как вероятность, то во втором \- исключение `IDebugExceptionEvent2` событие отправляется SDM.  В противном случае DE возобновляет выполнение программы и операционная система или среда выполнения обрабатывает исключение.  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)