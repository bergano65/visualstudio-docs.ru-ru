---
title: Попадание в точку останова | Документация Майкрософт
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152696"
---
# <a name="hitting-a-breakpoint"></a>Попадание в точку останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс, когда модуль отладки (DE) попадает на точку останова во время выполнения или шаг с заходом:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Устранение неполадок попаданий точки останова  
  
1. Отправляет DE [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) интерфейс как **EVENT_SYNC_STOP**.  
  
2. Диспетчер отладки сеансов (SDM) вызывает [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) получить точку останова, который был нажат.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
