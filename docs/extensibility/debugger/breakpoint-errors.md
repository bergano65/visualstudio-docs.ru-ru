---
title: Ошибки точки останова | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739214"
---
# <a name="breakpoint-errors"></a>Ошибки точки останова
Ниже описывается процесс, когда точка останова пытается выполнить привязку к коду, но завершается ошибкой.

## <a name="troubleshoot-a-breakpoint-error"></a>Устранение ошибки точки останова

1. Модуль отладки (DE) отправляет [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) в Диспетчер отладки сеансов (SDM).

2. Модель SDM вызывает [IDebugBreakpointErrorEvent2:: жетеррорбреакпоинт](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) для получения точки останова по ошибке.

3. Модель SDM вызывает [IDebugErrorBreakpoint2:: жетпендингбреакпоинт](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) для получения ожидающей точки останова, из которой поступила точка останова ошибки.

4. Модель SDM вызывает [IDebugErrorBreakpoint2:: жетбреакпоинтресолутион](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) , чтобы получить причину, по которой не удалось выполнить привязку точки останова по ошибке.

## <a name="see-also"></a>См. также раздел
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)
