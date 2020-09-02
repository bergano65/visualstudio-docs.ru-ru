---
title: Контекст вычисления выражения | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152783"
---
# <a name="expression-evaluation-context"></a>Контекст вычисления выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладке **контекст вычисления выражения**:  
  
- Представляет контекст для вычисления выражения. Как правило, контекст оценки соответствует лексической области, в которой оцениваются переменные, параметры, функции и методы. Например, контекст вычисления выражения, связанный с кадром стека, предоставит контекст для оценки локальных переменных, параметров метода и членов класса (если применимо).  
  
- Существует, когда программа остановлена в точке останова. Само выражение представляет собой структуру данных, представляющую проанализированное выражение, готовое к привязке и вычислению в заданном контексте.  
  
     Более подробно выражения создаются с помощью метода [парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . При вычислении выражения создается печатная строка, содержащая имя и тип переменной или аргумента и его значение. Эта строка отображается в окно контрольных значений или в окне "Локальные" интегрированной среды разработки.  
  
     При наличии `BSTR` интерфейса и [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) механизм отладки (de) может создать интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) путем синтаксического анализа выражения. При наличии `IDebugExpression2` интерфейса de может получить значение посредством синхронной или асинхронной оценки выражений. Это значение вместе с именем и типом переменной или аргумента отправляется в интегрированную среду разработки для вывода.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы оценки выражений](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
