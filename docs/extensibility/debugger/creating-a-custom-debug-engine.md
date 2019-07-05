---
title: Создание пользовательского модуля отладки | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3756eb105ec562d902d4631318e7a5fc698601a2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345305"
---
# <a name="create-a-custom-debug-engine"></a>Создание пользовательского модуля отладки
Отладчик (DE) — это компонент, позволяет выполнить отладку конкретного архитектур во время выполнения. Обычно имеется только одна реализация DE каждой среды выполнения.

> [!NOTE]
> Несмотря на наличие отдельных реализаций DE Transact-SQL и JScript, VBScript и JScript совместно используют один DE.

 DE работает с интерпретатором или операции система могла предоставлять такие операции отладки, как выполнение элемента управления, точки останова и оценки выражений. Эти службы реализуются с помощью интерфейсов DE и может вызвать отладчик для перехода между различные рабочие режимы. Дополнительные сведения см. в разделе [рабочие режимы](../../extensibility/debugger/operational-modes.md).

 Создание DE состоит из следующих действий:

1. Регистрация Развернутой с помощью Visual Studio

2. Включение программы для отладки

3. Реализовать выполнения элемента управления и состояние оценки

4. Отправка событий

5. Настройка завершение и отсоединение

## <a name="in-this-section"></a>Содержание раздела
 [Регистрация пользовательского модуля отладки](../../extensibility/debugger/registering-a-custom-debug-engine.md) объясняет шаги, необходимые для регистрации модуля отладки в Visual Studio, чтобы можно было использовать.

 [Включение программы для отладки](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) объясняет, что прежде чем ваши DE можно отлаживать программы, сначала необходимо запустить DE или присоединить ее к существующей программы.

 [Реализовать выполнения элемента управления и состоянии оценки](../../extensibility/debugger/execution-control-and-state-evaluation.md) описание, почему для отладки приложения требуется реализации выполнения функций управления.

 [Отправка событий](../../extensibility/debugger/sending-events.md) описывает взаимодействие между отладчиком и DE как модель событий на основании DCOM.

 [Настройка завершение и отсоединение](../../extensibility/debugger/termination-and-detaching.md) объясняется, как обеспечить нормальное завершение, это означает, что отсутствуют точки останова, исключения, ошибки времени выполнения или бесконечных циклов в приложении для отладки.

 [Вызов событий отладчика](../../extensibility/debugger/calling-debugger-events.md) Документирует вызывающий порядок событий, происходящих во время сеанса отладки.

 [Практическое руководство. Отладка пользовательского модуля отладки](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) описывается Отладка пользовательского DE.

## <a name="see-also"></a>См. также
- [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)