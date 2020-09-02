---
title: Ошибки точки останова | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e98dc5e4645ac67ecdf5ebb06ecf0f31510202e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147982"
---
# <a name="breakpoint-errors"></a>Ошибки точки останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описывается процесс, когда точка останова пытается выполнить привязку к коду, но завершается ошибкой:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Устранение ошибок точки останова  
  
1. Модуль отладки (DE) отправляет [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) в Диспетчер отладки сеансов (SDM).  
  
2. Модель SDM вызывает [IDebugBreakpointErrorEvent2:: жетеррорбреакпоинт](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) для получения точки останова по ошибке.  
  
3. Модель SDM вызывает [IDebugErrorBreakpoint2:: жетпендингбреакпоинт](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) для получения ожидающей точки останова, из которой поступила точка останова ошибки.  
  
4. Модель SDM вызывает [IDebugErrorBreakpoint2:: жетбреакпоинтресолутион](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) , чтобы получить причину, по которой не удалось выполнить привязку точки останова по ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
