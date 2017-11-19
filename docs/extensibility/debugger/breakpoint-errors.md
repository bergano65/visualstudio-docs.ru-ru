---
title: "Ошибки точки останова | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9c197bbaf8fb79ea4396c7b2e36af94d59c7ea8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoint-errors"></a>Ошибки точки останова
Ниже описан процесс, когда точки останова пытается выполнить привязку к коду, но произойдет ошибка:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Устранение ошибки точки останова  
  
1.  Модуль отладки (DE) отправляет [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) к диспетчеру сеанса отладки (SDM).  
  
2.  Вызовы SDM [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 ** `ppErrorBP`) для получения ошибки точки останова.  
  
3.  Вызовы SDM [IDebugErrorBreakpoint2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) для получения ожидающая точка останова, в котором возникла ошибка точки останова.  
  
4.  Вызовы SDM [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) для получения причины, почему не удалось выполнить привязку точки останова ошибок.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)