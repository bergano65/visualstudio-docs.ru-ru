---
title: Пошаговое выполнение в режиме приостановки выполнения | Документация Майкрософт
description: Сведения о процессе, который происходит, когда отладчик находится в режиме приостановки выполнения. Затем отладчик должен выполнить пошаговое выполнение кода.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f284fecf32a94f7187ecd34798f9ac21f476804
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960680"
---
# <a name="stepping-in-break-mode"></a>Пошаговое выполнение в режиме приостановки выполнения
В следующем разделе описывается процесс, выполняемый, когда отладчик находится в режиме приостановки выполнения и должен проходить код по шагам:

## <a name="stepping-process"></a>Процесс пошагового выполнения

1. Вызовите [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с аргументами [степкинд](../../extensibility/debugger/reference/stepkind.md) и [степунит](../../extensibility/debugger/reference/stepunit.md) , чтобы выполнить шаг.

2. По завершении действия отправьте [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.

## <a name="see-also"></a>См. также раздел
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
