---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "Интерфейс IDebugProgramNodeAttach2"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Позволяет узлу программы, уведомляемого попытки вложить в связанную программе.  
  
## Синтаксис  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется на одном и том же классе, который реализует IDebugProgramNode2 интерфейс получать уведомления операций присоединения и обеспечить возможность отмены операции присоединения.  
  
## Замечания для вызывающих объектов  
 Для получения этого интерфейса нужно вызвать метод `QueryInterface` метод  [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объект.  [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод должен быть вызван раньше  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод для предоставления узлу программы вероятность остановить процесс вложить.  
  
## Методы в том порядке Vtable  
 Этот интерфейс реализован следующий метод:  
  
|Метод|Описание|  
|-----------|--------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Вложение в связанную программе или откладывает вложение в процесс [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод.|  
  
## Заметки  
 Этот интерфейс является предпочтительной альтернативы нерекомендуемому [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) метод.  Все обработчики, всегда загружаются с отладки `CoCreateInstance` функция, т е они создаются вне адресного пространства, отлаживанными программы.  
  
 Если предыдущая реализация  `IDebugProgramNode2::Attach_V7` метод просто устанавливал  `GUID` программы, отлаживанными, затем лишь  [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) метод требуется реализовывать.  
  
 Если предыдущая реализация  `IDebugProgramNode2::Attach_V7` метод использует интерфейс обратного вызова, который был указан, то что необходимо переместить на реализацию описаний функциональности  [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) метод и  `IDebugProgramNodeAttach2` интерфейс должен быть реализован.  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)