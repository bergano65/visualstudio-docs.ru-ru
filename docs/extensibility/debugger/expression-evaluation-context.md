---
title: Контекст вычисления выражений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efaa678b5cbee763fabc9ccaf82c9322176b9102
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315239"
---
# <a name="expression-evaluation-context"></a>Контекст вычисления выражений
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки, **контекст вычисления выражений**:

- Представляет контекст для вычисления выражения. Как правило контекст вычисления соответствует лексическую область, в которой должно вычисляться переменные, параметры, функции и методы. Например контекст вычисления выражения, связанный с кадром стека будет обеспечить контекст для оценки локальных переменных, параметров методов и членов класса (если применимо).

- Возникает, когда программа остановлена в точке останова. Само выражение — это структура данных, представляющий проанализированное выражение, которое будет готов для привязки и оценке в рамках заданного контекста.

     В частности, выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод. При вычислении выражения, он создает печатные строка, содержащая имя и тип переменной или аргумента и его значение. Эта строка отображается в окне контрольных значений или в окне "Локальные" интегрированной среды разработки.

     Учитывая `BSTR` и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс, можно создать модуля отладки (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс путем синтаксического анализа выражения. Учитывая `IDebugExpression2` интерфейс, DE можно получить значение, полученное через синхронным или асинхронным выражениям. Это значение, а также имя и тип переменной или аргумента, отправляется в интегрированную среду разработки для отображения.

## <a name="see-also"></a>См. также
- [Интерфейсы оценки выражения](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)