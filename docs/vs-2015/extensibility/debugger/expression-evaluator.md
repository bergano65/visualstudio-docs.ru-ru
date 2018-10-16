---
title: Средство оценки выражений | Документация Майкрософт
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
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c65705cd38ef202d06e6461f59e5b4e5ae5c9a2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225294"
---
# <a name="expression-evaluator"></a>Вычислитель выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Вычислители выражений (EE) просмотрите синтаксис языка для синтаксического анализа и оценки переменных и выражений во время выполнения, что позволяет им быть просмотрен пользователем, когда IDE в режиме приостановки выполнения.  
  
## <a name="using-expression-evaluators"></a>С помощью вычислители выражений  
 Выражения создаются с помощью [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) метода, как показано ниже:  
  
1.  Модуль отладки (DE) реализует [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) интерфейс.  
  
2.  Возвращает размер пакета отладки `IDebugExpressionContext2` объекта из [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) интерфейс, а затем вызывает `IDebugStackFrame2::ParseText` метод его, чтобы получить [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) объекта.  
  
3.  Вызовы отладки пакета [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) метод или [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для получения значения выражения. `IDebugExpression2::EvaluateAsync` вызывается из окна команд и интерпретация. Все другие компоненты пользовательского интерфейса вызывать `IDebugExpression2::EvaluateSync`.  
  
4.  Результатом вычисления выражения является [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, который содержит имя, тип и значение результата вычисления выражения.  
  
 Во время вычисления выражения EE требует данные из компонент поставщика символов. Поставщик символов предоставляет символические сведения, используемые для определения и понимания проанализированное выражение.  
  
 По завершении оценки асинхронное выражение асинхронного события отправляет DE через диспетчер отладки сеансов (SDM) для уведомления IDE, что вычисление выражения завершения. После завершения синхронной выражение вычисления, результат вычисления возвращается из вызова `IDebugExpression2::EvaluateSync` метод.  
  
## <a name="implementation-notes"></a>Примечания по реализации  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Отладчиков ожидать, что дает возможность общаться с средство оценки выражений, с помощью интерфейсов Common Language Runtime (CLR). Таким образом, вычислитель выражений, работающее с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладчики должны поддерживать среды CLR (полный список всех интерфейсами отладки среды CLR можно найти в debugref.doc, входящий в состав из [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]).  
  
## <a name="see-also"></a>См. также  
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)

