---
title: "IDebugPortEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "Интерфейс IDebugPortEvents2"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс, уведомляет прослушивателя \(обычно сеанс отладки диспетчер \[SDM\] или обработчик отладки\) и создания и удаления программы на конкретном порте.  Эти сведения могут использоваться для представления в режиме реального времени представление процессов и программ, запущенных на порт.  
  
## Синтаксис  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## Примечания по реализации  
 Visual Studio обычно реализует этот интерфейс для получения уведомлений о создании и разрушении программы.  Отладчик может также реализовать данный интерфейс для прослушивания порта для таких событий.  
  
## Замечания для вызывающих объектов  
 Все [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейсы могут запросить  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс.  Then <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> метод  `IDebugPortEvents2` вызывает  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс, который требуется возвратить  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс.  Наконец, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метод  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> вызывается отправляемых через интерфейс события  [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md) метод.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны метод `IDebugPortEvents2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Отправляет события, которые описывают создание и разрушение процессов и программ на порт.|  
  
## Заметки  
 `IDebugPortEvents2` SDM также используется в процессе отладки программы, которые работают в котором уже отладки.  
  
 События порта передаются SDM этим интерфейсом.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)