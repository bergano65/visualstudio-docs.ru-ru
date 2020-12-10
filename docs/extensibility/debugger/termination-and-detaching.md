---
title: Завершение и отсоединение | Документация Майкрософт
description: Нормальное завершение означает, что отлаживаемая программа выполняется до завершения без точек останова, исключений, ошибок времени выполнения или бесконечного цикла.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 74ef32708374dd3fea4c181e85b9f67a239198ba
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995971"
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
В следующем разделе описывается нормальное завершение работы.

## <a name="discussion"></a>Разговор
 После продолжения работы интерфейса [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в случае отсутствия точек останова, исключений, ошибок времени выполнения или бесконечных циклов в приложении для отладки выполняется отладка программы до ее завершения. Этот процесс является нормальным завершением работы.

 Чтобы реализовать нормальное завершение, необходимо отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Для нормального завершения требуется выполнение метода [IDebugProgramDestroyEvent2:: жетекситкоде](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>См. также раздел
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
