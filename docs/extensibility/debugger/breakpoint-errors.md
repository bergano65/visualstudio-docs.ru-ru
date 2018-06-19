---
title: Ошибки точки останова | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e3c7271cc573388231045143f275d1032bef437
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099887"
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