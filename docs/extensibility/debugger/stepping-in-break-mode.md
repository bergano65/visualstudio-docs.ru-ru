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
ms.openlocfilehash: 66e7e227daa0dd58bf24ae946cce667992e09f90
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685031"
---
# <a name="stepping-in-break-mode"></a>Шаг с заходом в режиме приостановки выполнения
В следующем разделе описывается процесс, который возникает, когда отладчик находится в режиме приостановки выполнения и необходимо пошаговое выполнение кода:

## <a name="stepping-process"></a>Пошаговое выполнение процесса

1.  Вызовите [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с [STEPKIND](../../extensibility/debugger/reference/stepkind.md) и [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) аргументы для выполнения шага.

2.  По завершении шага отправки [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)