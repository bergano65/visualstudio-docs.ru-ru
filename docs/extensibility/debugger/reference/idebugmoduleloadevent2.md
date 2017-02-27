---
title: "IDebugModuleLoadEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModuleLoadEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugModuleLoadEvent2"
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugModuleLoadEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс передается с помощью обработчика отладки \(DE\) к сеансу отладки \(SDM\), если диспетчер будет загружен или будет выгружен модуль.  
  
## Синтаксис  
  
```  
IDebugModuleLoadEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, чтобы информировать, что был загружен или был выгружен модуль.   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события для оповещения о том, что был загружен или был выгружен модуль.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложенно для отлаживаемой программы.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны метод `IDebugModuleLoadEvent2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|Получает модуль, который загружается и выгружается.|  
  
## Заметки  
 Visual Studio использует это событие для хранения **Модули** окно последнее.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)