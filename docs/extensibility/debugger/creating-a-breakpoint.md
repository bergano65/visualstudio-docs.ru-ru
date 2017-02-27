---
title: "Создание точки останова | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "точки останова, создание"
  - "отладка [пакет SDK для отладки], создание точек останова"
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Создание точки останова
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс создать точку останова.  
  
## Методы созданию точки останова  
 Когда модуль, который требуется для связывания точка останова загружен, сеанс отладки вызовы диспетчера \(SDM\) следующие методы:  
  
1.  [IDebugPendingBreakpoint2:: Включить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2:: Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  CanBind вызывается, только если пользователь выполняет точку останова из окна точки останова.  
  
4.  [IDebugPendingBreakpoint2:: Создать привязку](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)