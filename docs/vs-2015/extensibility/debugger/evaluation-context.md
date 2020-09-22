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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843229"
---
# <a name="evaluation-context"></a>Контекст вычислений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда модуль отладки (DE) вызывает средство оценки выражений (EE), три аргумента, переданные в [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , определяют контекст для поиска и вычисления символов, как показано в следующей таблице.  
  
## <a name="arguments"></a>Аргументы  
  
|Аргумент|Описание|  
|--------------|-----------------|  
|`pSymbolProvider`|Интерфейс [идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md) , указывающий обработчик символов (SH), используемый для обозначения символа.|  
|`pAddress`|Интерфейс [идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md) , указывающий текущую точку выполнения. Это можно использовать для поиска метода, содержащего выполняемый код.|  
|`pBinder`|Интерфейс [идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md) , который можно использовать для поиска значения и типа символа по его имени.|  
  
 `IDebugParsedExpression::EvaluateSync` Возвращает интерфейс [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющий результирующее значение и его тип.  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы средства оценки ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
