---
title: Создание пользовательского модуля отладки | Документация Майкрософт
description: Используйте эти статьи, чтобы узнать о создании модуля отладки, который позволяет выполнять отладку определенных архитектур времени выполнения.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 673b08bf5680e04c90376c9eb3d63f6f03df9723
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914196"
---
# <a name="create-a-custom-debug-engine"></a>Создание пользовательского модуля отладки
Модуль отладки (DE) — это компонент, позволяющий выполнять отладку определенных архитектур времени выполнения. Как правило, для среды выполнения обычно используется только одна дереализация.

> [!NOTE]
> Хотя существуют отдельные реализации DE для Transact-SQL и JScript, VBScript и JScript совместно используют один DE.

 DE работает с интерпретатором или системой операций для предоставления таких служб отладки, как управление выполнением, точки останова и вычисление выражений. Эти службы реализуются через интерфейсы DE и могут привести к переходу отладчика между различными операционными режимами. Дополнительные сведения см. в разделе [Рабочие режимы](../../extensibility/debugger/operational-modes.md).

 Создание DE состоит из следующих шагов:

1. Регистрация DE в Visual Studio

2. Включение отладки программы

3. Реализация управления выполнением и оценки состояния

4. Отправка событий

5. Настройка завершения и отсоединения

## <a name="in-this-section"></a>В этом разделе
 [Регистрация пользовательского модуля отладки](../../extensibility/debugger/registering-a-custom-debug-engine.md) Описание действий, необходимых для регистрации модуля отладки в Visual Studio, чтобы его можно было использовать.

 [Включение отладки программы](../../extensibility/debugger/enabling-a-program-to-be-debugged.md) В этой статье объясняется, что перед началом отладки программы необходимо сначала запустить DE или присоединить ее к существующей программе.

 [Реализация управления выполнением и оценки состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md) Описывает, почему Отладка приложения требует реализации функций управления выполнением.

 [Отправка событий](../../extensibility/debugger/sending-events.md) Описывает взаимодействие между отладчиком и DE в качестве модели событий на основе DCOM.

 [Настройка завершения и отсоединения](../../extensibility/debugger/termination-and-detaching.md) Объясняет, как добиться нормального завершения, что означает отсутствие точек останова, исключений, ошибок времени выполнения или бесконечных циклов в приложении для отладки.

 [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md) Документирует порядок вызовов событий, происходящих в сеансе отладки.

 [Как выполнить отладку пользовательского модуля отладки](../../extensibility/debugger/how-to-debug-a-custom-debug-engine.md) Объясняется, как выполнить отладку пользовательского DE.

## <a name="see-also"></a>См. также раздел
- [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
