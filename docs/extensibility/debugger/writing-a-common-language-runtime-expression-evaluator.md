---
title: Написание общего языка Runtime Выражение Оценивателе (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712328"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Написание общего оценителя выражения времени выполнения языка
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Оценщик выражения (EE) является частью отладочего двигателя (DE), который обрабатывает синтаксис и семантику языка программирования, который произвел отладучку кода. Выражения должны оцениваться в контексте языка программирования. Например, в некоторых языках выражение «АЗБ» означает «сумма А и В». В других языках то же выражение может означать "А или В". Таким образом, для каждого языка программирования должен быть написан отдельный EE, который генерирует объектный код для отладки в IDE Visual Studio.

 Некоторые аспекты пакета отладок Visual Studio должны интерпретировать код в контексте языка программирования. Например, когда выполнение останавливается в точке разрыва, любые выражения, которые пользователь ввнедовал в окно **Watch,** должны быть оценены и отображены. Пользователь может изменить значение локальной переменной, введя выражение в окно **Watch** или в окно **Immediate.**

## <a name="in-this-section"></a>В этом разделе
 [Общий язык времени выполнения и оценки выражения](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Объясняет, что при интеграции запатентованного языка программирования в Visual Studio IDE написание EE, способного оценивать выражения в контексте запатентованного языка, позволяет компилировать сярприцию на промежуточный язык Microsoft (MSIL) без написания движка отладки.

 [Архитектура оценки экспрессии](../../extensibility/debugger/expression-evaluator-architecture.md) Обсуждает, как реализовать необходимые интерфейсы EE и вызвать общий язык запуска символа поставщика (SP) и связующего интерфейсов.

 [Регистрация оценщика выражений](../../extensibility/debugger/registering-an-expression-evaluator.md) Отмечается, что EE должен зарегистрироваться как фабрика классов как с общим временем выполнения языка, так и с средой выполнения Visual Studio.

 [Реализация оценщика выражения](../../extensibility/debugger/implementing-an-expression-evaluator.md) Описывает, как процесс оценки выражения включает в себя движок отладки (DE), поставщик символов (SP), объект связующего и оценщик выражения (EE).

 [Отображение местных жителей](../../extensibility/debugger/displaying-locals.md) Описывает, как при приостановке выполнения пакет отладки вызывает DE, чтобы получить список локальных переменных и аргументов.

 [Оценить выражение окна часов](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Документы, как пакет Visual Studio вызывает DE, чтобы определить текущее значение каждого выражения в своем списке наблюдения.

 [Изменение значения локального](../../extensibility/debugger/changing-the-value-of-a-local.md) Объясняет, что при изменении значения локального значения каждая строка окна Locals имеет связанный объект, который предоставляет имя, тип и текущее значение локального значения.

 [Реализация тип визуализаторов и пользовательских зрителей](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Объясняет, какой интерфейс должен быть реализован с помощью какого компонента для поддержки визуализаторов типов и пользовательских зрителей.

## <a name="see-also"></a>См. также
 [Эффектная студия отладчика расширяемые](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
