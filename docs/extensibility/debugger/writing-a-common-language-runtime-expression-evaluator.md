---
title: Написание распространенных вычислителя выражений среды CLR | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c295fcd881ed5348842355846c37af95b725f17e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348250"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Написание распространенных вычислителя выражений среды CLR
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Средство оценки выражений (EE) является частью модуля отладки (DE), который обрабатывает синтаксис и семантику языка программирования, которая является создателем отлаживаемого кода. Выражения необходимо вычислить в контексте языка программирования. Например, в некоторых языках, выражение «A + B» означает «сумму A и B.» На других языках то же выражение может означать «A или B.» Таким образом отдельного EE должно быть написано для каждого языка программирования, который создает объектный код для отладки в Интегрированной среде разработки Visual Studio.

 Некоторые аспекты пакета отладки Visual Studio необходимо интерпретировать код в контексте языка программирования. Например, если выполнение прекращается в точке останова, все выражения, введенные пользователем в **Watch** необходимо оценить и отображается окно. Пользователь может изменить значение локальной переменной, введя выражения в **Watch** окно или в **Интерпретация** окна.

## <a name="in-this-section"></a>Содержание раздела
 [Распространенные языковой среды выполнения и оценки выражений](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) объясняет, что при объединении собственный язык программирования в СРЕДЕ Visual Studio, написание EE для вычисления выражения в контексте языка можно скомпилировать в промежуточный язык Майкрософт (MSIL) без написания модуля отладки.

 [Архитектура вычислителя выражений](../../extensibility/debugger/expression-evaluator-architecture.md) описывает, как реализовать требуемые интерфейсы EE и вызывать общие поставщик символов среды выполнения языка (SP) и интерфейсов связывателя.

 [Регистрация вычислителя выражений](../../extensibility/debugger/registering-an-expression-evaluator.md) заметки, что EE необходимо зарегистрировать себя в качестве фабрику классов среды CLR и среды выполнения Visual Studio.

 [Реализация вычислителя выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md) описывает, как процесс вычисления выражения включает в себя модуль отладки (DE), поставщик символов (SP), объект модуля привязки и средство оценки выражений (EE).

 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md) описывает, как это сделать, когда выполнение приостанавливается, размер пакета отладки вызывает DE, чтобы получить список локальных переменных и аргументов.

 [Оценка выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md) документы, как размер пакета отладки Visual Studio вызывает DE для определения текущего значения каждого выражения в списке контрольных значений.

 [Изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md) объясняет, что изменение значения локальной переменной, окне "Локальные" каждая строка имеет связанный объект, который предоставляет имя, тип и текущего значения локальной переменной.

 [Реализация визуализаторов типов и пользовательских средств просмотра](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) объясняет, какие интерфейс должен реализовываться какой компонент для поддержки визуализаторов типов и пользовательских средств просмотра.

## <a name="see-also"></a>См. также
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)