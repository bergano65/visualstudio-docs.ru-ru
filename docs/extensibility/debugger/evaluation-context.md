---
title: "Контекст оценки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9a490ef7c4ea42fe85c291ee913d7ad5e1cda1bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="evaluation-context"></a>Контекст оценки
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда отладчик (DE) вызывает вычислитель выражений (EE), три аргументы, передаваемые [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) определить контекст для поиска и оценке символы, как показано в следующей таблице.  
  
## <a name="arguments"></a>Аргументы  
  
|Аргумент|Описание:|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) интерфейс, определяющий обработчик символ (SH) для использования с определением символа.|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) интерфейс, определяющий текущей точки выполнения. Это можно использовать для поиска метода, содержащего выполняемый код.|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) интерфейс, который может использоваться для поиска символов, заданную ее именем типа и значения.|  
  
 `IDebugParsedExpression::EvaluateSync`Возвращает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) интерфейс, представляющий результирующее значение и его тип.  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы вычислителя выражения ключа](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)