---
title: Создание пользовательского двигателя отугиваем (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementing
- debug engines, custom
- debugging [Debugging SDK], custom debug engines
ms.assetid: 52794238-6fae-451c-bf1c-99f344c6f173
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a350d640fffcc6e09cf8f981c797b97071a0cacf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739036"
---
# <a name="create-a-custom-debug-engine"></a>Создание пользовательского движка отладки
Отладка двигателя (DE) является компонентом, который позволяет отладки определенных архитектур времени выполнения. Как правило, на среду выполнения времени имеется только одна реализация DE.

> [!NOTE]
> Несмотря на то, что существуют отдельные реализации DE для Transact-S'L и JScript, VBScript и JScript имеют один общий обмен DE.

 DE работает с переводчиком или системой работы, чтобы обеспечить такие услуги отладки, как контроль выполнения, точки разрыва и оценка выражения. Эти службы реализуются через интерфейсы DE и могут привести к переходу отладчика между различными режимами работы. Для получения дополнительной [информации см.](../../extensibility/debugger/operational-modes.md)

 Создание DE состоит из следующих шагов:

1. Регистрация DE с Visual Studio

2. Включить отладку программы

3. Реализация контроля исполнения и оценки состояния

4. Отправка событий

5. Настройка прекращения и отсоединения

## <a name="in-this-section"></a>В этом разделе
 [Регистрация пользовательского двигателя отладки](../../extensibility/debugger/registering-a-custom-debug-engine.md) Объясняет шаги, необходимые для регистрации отладки двигателя с Visual Studio, так что он может быть использован.

 [Включить отладку программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) Объясняет, что прежде чем ваш DE может отладить программу, вы должны сначала запустить DE или прикрепить его к существующей программе.

 [Реализация контроля исполнения и оценки состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md) Обсуждается, почему отладка приложения требует реализации функций управления выполнением.

 [Отправка событий](../../extensibility/debugger/sending-events.md) Описывает связь между отладчиком и DE как модель событий, основанная на DCOM.

 [Настройка прекращения и отсоединения](../../extensibility/debugger/termination-and-detaching.md) Объясняет, как достичь нормального завершения, что означает отсутствие моментов разрыва, исключений, ошибок времени выполнения или бесконечных циклов в приложении, которые будут отдипированы.

 [События отладки вызова](../../extensibility/debugger/calling-debugger-events.md) Документирует порядок вызова событий, происходящих в сеансе отладки.

 [Как: отладить пользовательский движок отладки](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Объясняет, как отладить пользовательский DE.

## <a name="see-also"></a>См. также
- [Эффектная студия отладчика расширяемые](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
