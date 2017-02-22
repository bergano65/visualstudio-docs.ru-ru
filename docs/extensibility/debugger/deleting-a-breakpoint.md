---
title: "Удаление точки останова | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "точки останова, удаление"
  - "отладка [пакет SDK для отладки], удаление точки останова"
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Удаление точки останова
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс удаления ожидается точка останова.  
  
## Процесс удаления  
 Сеанс отладки вызовы диспетчера \(SDM\) [IDebugPendingBreakpoint2:: Удалить](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) метод удаления ожидается привязанные точку останова и все связанные точки останова из нее.  
  
> [!NOTE]
>  Одну связанную точка останова может быть также удаляется вызовом [IDebugBoundBreakpoint2:: Удалить](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)