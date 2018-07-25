---
title: Контекст вычисления выражений | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a01d8fd9e1ac7a439898775bc8b4b0fc933650c
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232498"
---
# <a name="expression-evaluation-context"></a>Контекст вычисления выражений
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки, **контекст вычисления выражений**:  
  
-   Представляет контекст для вычисления выражения. Как правило контекст вычисления соответствует лексическую область, в которой должно вычисляться переменные, параметры, функции и методы. Например контекст вычисления выражения, связанный с кадром стека будет обеспечить контекст для оценки локальных переменных, параметров методов и членов класса (если применимо).  
  
-   Возникает, когда программа остановлена в точке останова. Само выражение — это структура данных, представляющий проанализированное выражение, которое будет готов для привязки и оценке в рамках заданного контекста.  
  
     В частности, выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод. При вычислении выражения, он создает печатные строка, содержащая имя и тип переменной или аргумента и его значение. Эта строка отображается в окне контрольных значений или в окне "Локальные" интегрированной среды разработки.  
  
     Учитывая `BSTR` и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс, можно создать модуля отладки (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс путем синтаксического анализа выражения. Учитывая `IDebugExpression2` интерфейс, DE можно получить значение, полученное через синхронным или асинхронным выражениям. Это значение, а также имя и тип переменной или аргумента, отправляется в интегрированную среду разработки для отображения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)