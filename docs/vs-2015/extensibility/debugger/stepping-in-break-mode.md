---
title: Шаг с заходом в режиме приостановки выполнения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423365"
---
# <a name="stepping-in-break-mode"></a>Пошаговое выполнение в режиме приостановки выполнения
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ниже описывается процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и необходимо пошаговое выполнение кода:  
  
## <a name="stepping-process"></a>Пошаговое выполнение процесса  
  
1. Вызовите [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с [STEPKIND](../../extensibility/debugger/reference/stepkind.md) и [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) аргументы для выполнения шага.  
  
2. По завершении шага отправки [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
