---
title: Стратегии реализации вычислителя выражений | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67b2496c2e30428cd4cc830526e53cf0cc61fdd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator-implementation-strategy"></a>Стратегии реализации вычислителя выражений
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Один из способов создания вычислитель выражений (Эстония) требуется реализовать минимальный код, необходимый для отображения локальных переменных в **локальные** окна. Полезно понимать, что каждая строка в **локальные** окне отображается имя, тип и значение локальной переменной, и все три представлены [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объекта. Имя, тип и значение локальной переменной можно получить из `IDebugProperty2` , вызывая его [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод. Дополнительные сведения об отображении локальных переменных в **локальные** окна, в разделе [отображение локальные](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Обсуждение  
 Возможная реализация последовательность начинается с реализации [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) и [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) методы должны быть реализованы для отображения локальных переменных. Вызов `IDebugExpressionEvaluator::GetMethodProperty` возвращает `IDebugProperty2` объект, представляющий метод: то есть [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) объекта. Методы сами не отображаются в **локальные** окна.  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) метод должен быть реализован рядом. Модуль отладки (DE) вызывает этот метод, чтобы получить список локальных переменных и аргументов, передав `IDebugProperty2::EnumChildren` `guidFilter` аргумент `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` вызовы [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) и [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), объединение результатов в одном перечисления. В разделе [отображение локальные](../../extensibility/debugger/displaying-locals.md) для получения дополнительных сведений.  
  
## <a name="see-also"></a>См. также  
 [Реализация вычислитель выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)