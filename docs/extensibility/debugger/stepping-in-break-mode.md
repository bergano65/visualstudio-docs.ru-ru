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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80273bf470a3ed0c342e781085de6e991508451c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845197"
---
# <a name="stepping-in-break-mode"></a>Пошаговое выполнение в режиме приостановки выполнения
В следующем разделе описывается процесс, выполняемый, когда отладчик находится в режиме приостановки выполнения и должен проходить код по шагам:

## <a name="stepping-process"></a>Процесс пошагового выполнения

1. Вызовите [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) с аргументами [степкинд](../../extensibility/debugger/reference/stepkind.md) и [степунит](../../extensibility/debugger/reference/stepunit.md) , чтобы выполнить шаг.

2. По завершении действия отправьте [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) как событие остановки.

## <a name="see-also"></a>См. также раздел
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
