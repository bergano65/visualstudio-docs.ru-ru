---
title: Написание распространенных вычислителя выражений среды CLR | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfd368bb0302fec1fcf9fdd1f6e6e069377846ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783016"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Запись вычислителя выражений среды CLR
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Средство оценки выражений (EE) является частью модуля отладки (DE), который обрабатывает синтаксис и семантику языка программирования, которая является создателем отлаживаемого кода. Выражения необходимо вычислить в контексте языка программирования. Например, в некоторых языках, выражение «A + B» означает «сумму A и B.» На других языках то же выражение может означать «A или B.» Таким образом отдельного EE должно быть написано для каждого языка программирования, который создает объектный код для отладки в Интегрированной среде разработки Visual Studio.  
  
 Некоторые аспекты пакета отладки Visual Studio необходимо интерпретировать код в контексте языка программирования. Например, если выполнение прекращается в точке останова, все выражения, введенные пользователем в **Watch** необходимо оценить и отображается окно. Кроме того, он может изменять значение локальной переменной, введя выражения в **Watch** окно или в **Интерпретация** окна.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Вычисления выражений и среда CLR](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Объясняет, что при объединении собственный язык программирования в СРЕДЕ Visual Studio, написание EE для вычисления выражения в контексте языка позволяет скомпилировать в промежуточный язык Майкрософт (MSIL) без написания модуля отладки.  
  
 [Архитектура вычислителя выражений](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Описывает, как реализовать требуемые интерфейсы EE и вызывать общие поставщик символов среды выполнения языка (SP) и интерфейсов связывателя.  
  
 [Регистрация вычислителя выражений](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Отмечает, что EE необходимо зарегистрировать себя в качестве фабрику классов среды CLR и среды выполнения Visual Studio.  
  
 [Реализация вычислителя выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Описывает, как процесс вычисления выражения включает в себя модуль отладки (DE), поставщик символов (SP), объект модуля привязки и средство оценки выражений (EE).  
  
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)  
 Описывает, как это сделать, когда выполнение приостанавливается, размер пакета отладки вызывает DE, чтобы получить список локальных переменных и аргументов.  
  
 [Вычисление выражения окна контрольных значений](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Описывает, как размер пакета отладки Visual Studio вызывает DE для определения текущего значения каждого выражения в его список наблюдения за.  
  
 [Изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Объясняет, что изменение значения локальной переменной, окне "Локальные" каждая строка имеет связанный объект, который предоставляет имя, тип и текущего значения локальной переменной.  
  
 [Реализация визуализаторов типов и пользовательских средств просмотра](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Объясняет, какие интерфейс должен реализовываться какой компонент для поддержки визуализаторов типов и пользовательских средств просмотра.  
  
## <a name="see-also"></a>См. также  
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

