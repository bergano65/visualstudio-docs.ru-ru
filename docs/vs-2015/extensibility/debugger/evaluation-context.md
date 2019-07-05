---
title: Контекст оценки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7dae6ddcb0c75f0dcbc2207465aed522a4210159
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444759"
---
# <a name="evaluation-context"></a>Контекст вычислений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда модуль отладки (DE) вызывает средство оценки выражений (EE), три аргументы, передаваемые в [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) определить контекст для поиск и пробное использование символов, как показано в следующей таблице.  
  
## <a name="arguments"></a>Аргументы  
  
|Аргумент|Описание|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) интерфейс, который задает обработчик символов (SH) для использования для идентификации символа.|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) интерфейс, определяющий текущей точки выполнения. Это можно использовать для поиска метода, содержащего выполняемый код.|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) интерфейс, который может использоваться для поиска, значение и тип символа, заданную ее именем.|  
  
 `IDebugParsedExpression::EvaluateSync` Возвращает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий результирующее значение и его тип.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычислителя ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
