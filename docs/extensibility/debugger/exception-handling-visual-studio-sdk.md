---
title: Исключение, обработка (пакет SDK для Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b580a4774cfe06f81e2d9798ef6cf949afe8c1c8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710855"
---
# <a name="exception-handling-visual-studio-sdk"></a>Обработка исключений (Visual Studio SDK)
Ниже описывается процесс, происходящее при возникновении исключения.

## <a name="exception-handling-process"></a>Процесс обработки исключений

1.  Когда исключение, но прежде чем он обрабатывается обработчиком исключений в отлаживаемой программы, модуль отладки (DE) отправляет [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) в диспетчер отладки сеансов (SDM) как событие остановки. `IDebugExceptionEvent2` Отправляется, если только параметры для исключения (указано в диалоговом окне "исключения" в пакете отладки) укажите, что пользователь хочет остановить при возникновении уведомления о первом этапе обработки исключений.

2.  Вызовы SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) для получения свойства исключения.

3.  Вызовы отладки пакета [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) для определения, какие параметры пользователя.

4.  Размер пакета отладки запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно исключения первого шанса.

5.  Если пользователь выбрал в том продолжить, SDM вызывает [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    -   Если метод возвращает значение S_OK, вызывает [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         - или -

         Если метод возвращает значение S_FALSE, программа отлаживаемой дается второй шанс для обработки исключения.

6.  Если отлаживаемой программы не имеет обработчика для второй возможности захвата исключения, DE отправляет `IDebugExceptionEvent2` для SDM как **EVENT_SYNC_STOP**.

7.  Размер пакета отладки запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно исключения первого шанса.

8.  Вызовы отладки пакета [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) для определения, какие параметры пользователя.

9. Размер пакета отладки запрашивает у пользователя, как обрабатывать исключения, открыв диалоговое окно второй возможности захвата исключений.

10. Если метод возвращает значение S_OK, вызывает `IDebugExceptionEvent2::PassToDebuggee`.

## <a name="see-also"></a>См. также
- [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md)