---
title: Обработка исключений (Визуальная студия SDK) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738762"
---
# <a name="exception-handling-visual-studio-sdk"></a>Обработка исключений (Visual Studio SDK)
Ниже описывается процесс, который происходит при броске исключений.

## <a name="exception-handling-process"></a>Процесс обработки исключений

1. При первом бросе исключение, но до того, как оно будет обработано обработчиком исключений в отладке программы, движок отладки (DE) отправляет [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) менеджеру отладки сеанса (SDM) в качестве события остановки. Отправка, `IDebugExceptionEvent2` если только настройки для исключения (указанные в диалоговом поле Исключений в пакете отладок) указывают, что пользователь хочет остановиться на уведомлениях об исключении первого шанса.

2. SDM вызывает [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) для того чтобы получить свойство исключения.

3. Пакет отладки вызывает [IDebugExceptionEvent2::CanPassToDebuggee,](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) чтобы определить, какие варианты представить пользователю.

4. Пакет отладки спрашивает пользователя, как обрабатывать исключение, открывая диалоговую коробку исключения первого шанса.

5. Если пользователь решит продолжить работу, SDM вызывает [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Если метод возвращается S_OK, звонит [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -или-

         Если метод возвращается S_FALSE, отладить программу предоставляется второй шанс для обработки исключения.

6. Если отладка программы не имеет обработчика для исключения второго шанса, DE отправляет в `IDebugExceptionEvent2` SDM в качестве **EVENT_SYNC_STOP.**

7. Пакет отладки спрашивает пользователя, как обрабатывать исключение, открывая диалоговую коробку исключения первого шанса.

8. Пакет отладки вызывает [IDebugExceptionEvent2::CanPassToDebuggee,](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) чтобы определить, какие варианты представить пользователю.

9. Пакет отладки спрашивает пользователя, как обрабатывать исключение, открывая поле диалога исключения второго шанса.

10. Если метод возвращается `IDebugExceptionEvent2::PassToDebuggee`S_OK, вызовы .

## <a name="see-also"></a>См. также
- [События отладки вызова](../../extensibility/debugger/calling-debugger-events.md)
