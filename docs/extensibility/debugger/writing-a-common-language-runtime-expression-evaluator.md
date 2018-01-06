---
title: "Запись общих вычислитель выражений языка среды выполнения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d52a9dbed6cec64426247a0b92bff2b8ec98ec97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Создание общих вычислитель выражений языка среды выполнения
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Средство оценки выражений (Эстония) является частью модуля отладки (DE), который обрабатывает синтаксис и семантику языка программирования, создавший отлаживаемого кода. Оценка выражения должна выполняться в контексте языка программирования. Например, в некоторых языках, выражение «A + B» означает «сумма A и B.» В других языках то же выражение может означать «A или B.» Таким образом отдельные EE должно быть написано для каждого языка программирования, который создает объектный код для отладки в Интегрированной среде разработки Visual Studio.  
  
 Некоторые аспекты отладочный пакет Visual Studio необходимо интерпретировать код в контексте языка программирования. Например, при выполнение останавливается в точке останова все выражения, введенные пользователем в **Контрольные значения** необходимо оценить и отображается окно. Кроме того, пользователь может изменить значение локальной переменной, введите выражение в **Контрольные значения** окно или в **Интерпретация** окна.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Вычисления выражений и среда CLR](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Объясняет, что при объединении собственный язык программирования в СРЕДЕ Visual Studio, написание EE поддерживает вычисление выражений в контексте элемента языка позволяет компилируются в промежуточный язык Microsoft (MSIL) без написания модуля отладки.  
  
 [Архитектура вычислителя выражений](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Описывает, как реализовать необходимые интерфейсы EE и вызывать общие языка среды выполнения символ поставщика услуг и интерфейсы связывателя.  
  
 [Регистрация вычислителя выражений](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Обращает внимание, что EE должен зарегистрироваться как фабрика класса среды CLR и среды выполнения Visual Studio.  
  
 [Реализация вычислителя выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Описывает, как процесс вычисления выражения включает в себя модуль отладки (DE), символ поставщика услуг, объект модуля привязки и средство оценки выражений (EE).  
  
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)  
 Описывает, как это сделать, если выполнение приостанавливается, отладочный пакет вызывает DE, чтобы получить список локальных переменных и аргументов.  
  
 [Вычисление выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Документирует как отладочный пакет Visual Studio вызывает DE, чтобы определить текущее значение каждого выражения в списке контрольных значений.  
  
 [Изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Объясняет, что в подходящее значение для локальной, каждой строки в окне «Локальные» имеет связанный объект, который предоставляет имя, тип и текущее значение локального.  
  
 [Реализация визуализаторов типов и пользовательских средств просмотра](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Описывается интерфейс, который должен быть реализован, какой компонент для поддержки визуализаторами типов и пользовательских средств просмотра.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)