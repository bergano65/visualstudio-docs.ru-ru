---
title: Попадание в точку останова | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4b5805621d1fd58f6c5d39c779e6b87719edac6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214985"
---
# <a name="hitting-a-breakpoint"></a>Попадание в точку останова
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описан процесс, когда модуль отладки (DE) попадает на точку останова во время выполнения или шаг с заходом:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Устранение неполадок попаданий точки останова  
  
1.  Отправляет DE [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) интерфейс как **EVENT_SYNC_STOP**.  
  
2.  Диспетчер отладки сеансов (SDM) вызывает [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) получить точку останова, который был нажат.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)

