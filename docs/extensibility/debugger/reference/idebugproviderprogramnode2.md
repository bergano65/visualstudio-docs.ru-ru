---
title: "IDebugProviderProgramNode2 | Microsoft Docs"
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
  - "IDebugProviderProgramNode2"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2"
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс программа\-родственные маршалирует интерфейсы через границы процессов.  
  
## Синтаксис  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс на одном и том же объекта, реализующего IDebugProgramNode2 поддерживать интерфейсы маршалинга через границы процессов.  
  
## Замечания для вызывающих объектов  
 Вызов [QueryInterface](/visual-cpp/atl/queryinterface) на  `IDebugProgramNode2` интерфейс для получения этого интерфейса.  Если этот интерфейс не может быть получен, то DE не поддерживает маршалинг интерфейсов.  
  
## Методы в том порядке Vtable  
 Этот интерфейс реализован следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Возвращает указанный интерфейс через границы процессов.|  
  
## Заметки  
 Этот интерфейс реализуется, когда выполняется DE в отдельном пространстве процесса от отлаживанными программы: например, если DE работает в пространстве процесса Visual Studio, а не пространства процесса отлаживаемой программы.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)