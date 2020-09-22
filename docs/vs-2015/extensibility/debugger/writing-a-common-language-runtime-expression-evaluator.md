---
title: Написание средства оценки выражений среды CLR | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 961a4d646a61fedda381f9451902b3bcdcc956d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843009"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Запись вычислителя выражений среды CLR
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Средство оценки выражений (EE) является частью модуля отладки (DE), который обрабатывает синтаксис и семантику языка программирования, создавшего отлаживаемый код. Выражения должны оцениваться в контексте языка программирования. Например, в некоторых языках выражение «A + B» означает «сумму A и б». В других языках одно и то же выражение может означать "A или B". Поэтому отдельный EE должен быть написан для каждого языка программирования, который создает объектный код для отладки в интегрированной среде разработки Visual Studio.  
  
 Некоторые аспекты пакета отладки Visual Studio должны интерпретировать код в контексте языка программирования. Например, при остановке выполнения в точке останова все выражения, вводимые пользователем в окно **контрольных значений** , должны оцениваться и отображаться. Кроме того, пользователь может изменить значение локальной переменной, введя выражение в окно **контрольных значений** или в окно **Immediate** .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Вычисления выражений и среда CLR](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Объясняется, что при интеграции собственного языка программирования в интегрированную среду разработки Visual Studio написание EE с поддержкой оценки выражений в контексте собственного языка позволяет компилироваться на языке MSIL без написания модуля отладки.  
  
 [Архитектура вычислителя выражений](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Описывает, как реализовать требуемые интерфейсы EE и вызывать интерфейсы поставщика символов среды CLR (SP) и связывателя.  
  
 [Регистрация вычислителя выражений](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Заметок о том, что EE должен зарегистрировать себя как фабрика класса как в среде CLR, так и в среде выполнения Visual Studio.  
  
 [Реализация вычислителя выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Описывает, как процесс вычисления выражения включает в себя модуль отладки (DE), поставщик символов (SP), объект связывателя и средство оценки выражений (EE).  
  
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)  
 Описывает, как, когда выполнение приостанавливается, пакет отладки вызывает метод DE для получения списка локальных переменных и аргументов.  
  
 [Вычисление выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Документируется, как пакет отладки Visual Studio вызывает метод DE для определения текущего значения каждого выражения в его списке контрольных значений.  
  
 [Изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Объясняется, что при изменении значения локальной каждой строки в окне Локальные переменные имеется связанный объект, предоставляющий имя, тип и текущее значение локального объекта.  
  
 [Реализация визуализаторов типов и пользовательских средств просмотра](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Описывает интерфейс, который должен быть реализован компонентом для поддержки визуализаторов типов и пользовательских средств просмотра.  
  
## <a name="see-also"></a>См. также:  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
