---
title: "IDebugProgramDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2"
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс передается с помощью обработчика отладки \(DE\) к сеансу отладки \(SDM\), если диспетчер выполнения программы до завершения.  
  
## Синтаксис  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE или пользовательского поставщика порта, реализующие этот интерфейс, чтобы информировать, что программа была завершена и больше недоступны для отладки.   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  
  
## Замечания для вызывающих объектов  
 DE или пользовательского поставщика порта создают и выполняют этот объект события для оповещения завершение программы.  Отправляет данное событие с помощью DE IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложило в отлаживаемом программе.  Пользовательский поставщик отправляет данное событие использование порта [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейс.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны метод `IDebugProgramDestroyEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md)|Возвращает код завершения программы.|  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)