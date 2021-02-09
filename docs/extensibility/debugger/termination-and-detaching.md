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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ac3e8517ee99dcd52261eb87b6cee3954793d3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895899"
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
В следующем разделе описывается нормальное завершение работы.

## <a name="discussion"></a>Разговор
 После продолжения работы интерфейса [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в случае отсутствия точек останова, исключений, ошибок времени выполнения или бесконечных циклов в приложении для отладки выполняется отладка программы до ее завершения. Этот процесс является нормальным завершением работы.

 Чтобы реализовать нормальное завершение, необходимо отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Для нормального завершения требуется выполнение метода [IDebugProgramDestroyEvent2:: жетекситкоде](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>См. также раздел
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
