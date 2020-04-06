---
title: Прекращение и отсоединение Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b88255d618ce42fa55d878f192d31523ba3f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712497"
---
# <a name="termination-and-detaching"></a>Прекращение и отсоединение
В следующем разделе описывается нормальное прекращение.

## <a name="discussion"></a>Обсуждение
 После того, как интерфейс [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) продолжится, если нет моментов разрыва, исключений, ошибок времени выполнения или бесконечных циклов в приложении, которые будут отлажены, программа, которая будет отлажена, выполняется до завершения. Этот процесс является нормальным прекращением.

 Для реализации нормального прекращения необходимо отправить [IDebugProgramDestroyEvent2.](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) Нормальное прекращение требует запуска метода [IDebugProgramDestroyEvent2::GetExitCode.](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)

## <a name="see-also"></a>См. также
- [Создание пользовательского движка отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
