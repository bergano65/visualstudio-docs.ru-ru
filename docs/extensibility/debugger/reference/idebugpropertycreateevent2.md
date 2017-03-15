---
title: "IDebugPropertyCreateEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyCreateEvent2"
helpviewer_keywords: 
  - "Интерфейс IDebugPropertyCreateEvent2"
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс передается с помощью обработчика отладки \(DE\) к сеансу отладки \(SDM\) диспетчер при создании свойство, связанное с указанным документом.  
  
## Синтаксис  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 DE реализующий этот интерфейс, чтобы информировать, что свойство было создано.   IDebugEvent2 интерфейс должен быть реализован в одном объекте, как этот интерфейс.  SDM использует [QueryInterface](/visual-cpp/atl/queryinterface) доступ  `IDebugEvent2` интерфейс.  Этот интерфейс реализуется если DE создал свойство, связанное со скриптом, который был загружен или был создан и если этому скрипту будет отображаться в интегрированную среду разработки.  
  
## Замечания для вызывающих объектов  
 DE создает и отправляет этот объект события для оповещения о том, что свойство было создано.  Событие отправляется с помощью IDebugEventCallback2 функция обратного вызова, предоставленные SDM, когда он вложенно для отлаживаемой программы.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны метод `IDebugPropertyCreateEvent2` интерфейс.  
  
|Метод|Описание|  
|-----------|--------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Возвращает новое свойство.|  
  
## Заметки  
 Если свойство имеет отдельный документ или скрипт, связанные с ним, DE может отправлять данное событие для SDM для обновления **Документы скриптов** окно с именем документа.  SDM без доставки [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) с аргументом  `guidDocument` получение a  `VARIANT` содержаться  [IUnknown](/visual-cpp/atl/iunknown) указатель.  SDM без доставки [QueryInterface](/visual-cpp/atl/queryinterface) для этого указателя для извлечения  [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс, который используется для обновления  **Документы скриптов** окна.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)