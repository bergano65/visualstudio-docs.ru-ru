---
title: Шаг с заходом в режиме приостановки выполнения | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fff7edc494c763407c65785fe1de0b3fd77d7b2
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276511"
---
# <a name="stepping-in-break-mode"></a>Шаг с заходом в режиме приостановки выполнения
В следующем разделе описывается процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и необходимо пошаговое выполнение кода:  
  
## <a name="stepping-process"></a>Пошаговое выполнение процесса  
  
1.  Вызовите [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с [STEPKIND](../../extensibility/debugger/reference/stepkind.md) и [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) аргументы для выполнения шага.  
  
2.  По завершении шага отправки [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.  
  
## <a name="see-also"></a>См. также  
 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)