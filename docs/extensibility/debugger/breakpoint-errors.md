---
title: "Ошибки точки останова | Microsoft Docs"
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
  - "точки останова, ошибки"
  - "отладка [пакет SDK для отладки], точки останова"
  - "ошибки [пакет SDK для отладки]"
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Ошибки точки останова
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс, если точка останова пытается привязать к коду, но ошибка:  
  
## Устранение неполадок ошибка точки останова  
  
1.  Отладчик \(DE\) отправляет IDebugBreakpointErrorEvent2 к сеансу отладки \(SDM manager\).  
  
2.  Вызовы SDM [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) \(IDebugErrorBreakpoint2 \*\*  `ppErrorBP`\) получить точку останова ошибки.  
  
3.  Вызовы SDM [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) получить завершения отложенной точку останова, из которой была создана точка останова ошибки.  
  
4.  Вызовы SDM [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) получить причину сбоя точка останова ошибки не удалось выполнить привязку.  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)