---
title: Достижение точки останова | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152696"
---
# <a name="hitting-a-breakpoint"></a>Попадание в точку останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описывается процесс, когда модуль отладки (DE) достигает точки останова при выполнении или пошаговом выполнении.  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Устранение неполадок точки останова  
  
1. Параметр DE отправляет интерфейс [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) в качестве **EVENT_SYNC_STOP**.  
  
2. Диспетчер отладки сеансов (SDM) вызывает [IDebugBreakpointEvent2::: енумбреакпоинтс](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) для получения точки останова, которая была достигнута.  
  
## <a name="see-also"></a>См. также:  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
