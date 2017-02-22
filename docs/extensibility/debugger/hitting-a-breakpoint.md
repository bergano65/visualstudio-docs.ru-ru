---
title: "Попадание в точку останова | Microsoft Docs"
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
  - "отладка [пакет SDK для отладки], прерывания в точках останова"
  - "точки останова, нажав клавишу"
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Попадание в точку останова
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Далее описывается процесс, когда обработчик отладки \(DE\) ударяет точку останова во время выполнения или шагающ:  
  
## Устранение неполадок точка останова попадания  
  
1.  DE отправляет [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) интерфейс как  **EVENT\_SYNC\_STOP**.  
  
2.  Сеанс отладки вызовы диспетчера \(SDM\) [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) получить точку останова, которая была выполненного строкой.  
  
## См. также  
 [Вызов события отладчика](../../extensibility/debugger/calling-debugger-events.md)