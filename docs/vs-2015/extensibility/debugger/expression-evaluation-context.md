---
title: Контекст вычисления выражений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377609cb9f971b667872c198a53b45a6288f2c15
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052928"
---
# <a name="expression-evaluation-context"></a>Контекст вычисления выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки, **контекст вычисления выражений**:  
  
- Представляет контекст для вычисления выражения. Как правило контекст вычисления соответствует лексическую область, в которой должно вычисляться переменные, параметры, функции и методы. Например контекст вычисления выражения, связанный с кадром стека будет обеспечить контекст для оценки локальных переменных, параметров методов и членов класса (если применимо).  
  
- Возникает, когда программа остановлена в точке останова. Само выражение — это структура данных, представляющий проанализированное выражение, которое будет готов для привязки и оценке в рамках заданного контекста.  
  
     В частности, выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метод. При вычислении выражения, он создает печатные строка, содержащая имя и тип переменной или аргумента и его значение. Эта строка отображается в окне контрольных значений или в окне "Локальные" интегрированной среды разработки.  
  
     Учитывая `BSTR` и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс, можно создать модуля отладки (DE) [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) интерфейс путем синтаксического анализа выражения. Учитывая `IDebugExpression2` интерфейс, DE можно получить значение, полученное через синхронным или асинхронным выражениям. Это значение, а также имя и тип переменной или аргумента, отправляется в интегрированную среду разработки для отображения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы оценки выражения](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
