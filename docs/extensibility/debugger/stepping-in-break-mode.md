---
title: Шаг с заходом в режиме приостановки выполнения | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4aefa1c4b3767ae58cb526c6f5a663350efd3137
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922877"
---
# <a name="stepping-in-break-mode"></a>Шаг с заходом в режиме приостановки выполнения
В следующем разделе описывается процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и необходимо пошаговое выполнение кода:  
  
## <a name="stepping-process"></a>Пошаговое выполнение процесса  
  
1.  Вызовите [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с [STEPKIND](../../extensibility/debugger/reference/stepkind.md) и [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) аргументы для выполнения шага.  
  
2.  По завершении шага отправки [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)