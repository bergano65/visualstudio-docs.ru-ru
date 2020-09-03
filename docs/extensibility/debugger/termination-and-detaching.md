---
title: Завершение и отсоединение | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712497"
---
# <a name="termination-and-detaching"></a>Завершение и отсоединение
В следующем разделе описывается нормальное завершение работы.

## <a name="discussion"></a>Разговор
 После продолжения работы интерфейса [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) или [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) в случае отсутствия точек останова, исключений, ошибок времени выполнения или бесконечных циклов в приложении для отладки выполняется отладка программы до ее завершения. Этот процесс является нормальным завершением работы.

 Чтобы реализовать нормальное завершение, необходимо отправить [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) . Для нормального завершения требуется выполнение метода [IDebugProgramDestroyEvent2:: жетекситкоде](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) .

## <a name="see-also"></a>См. также раздел
- [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)
