---
title: Стратегия реализации вычислителя выражений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421164"
---
# <a name="expression-evaluator-implementation-strategy"></a>Стратегия реализации вычислителя выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Один из способов создания вычислитель выражений (EE) является сначала реализация минимальный код, необходимый для отображения локальных переменных в **"Локальные"** окна. Полезно понимать, что каждая строка в **"Локальные"** окне отображается имя, тип и значение локальной переменной, и все три представленных [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объекта. Имя, тип и значение локальной переменной можно получить из `IDebugProperty2` , вызвав его [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) метод. Дополнительные сведения о том, как для отображения локальных переменных в **"Локальные"** окно, см. в разделе ["Локальные" Отображение](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Обсуждение  
 Возможная реализация последовательность начинается с реализации [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). [Проанализировать](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) и [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) методы должны быть реализованы для отображения локальных переменных. Вызов `IDebugExpressionEvaluator::GetMethodProperty` возвращает `IDebugProperty2` , представляющий метод: то есть [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) объекта. Сами методы не отображаются в **"Локальные"** окна.  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) метод должен быть реализован рядом. Модуль отладки (DE) вызывает этот метод, чтобы получить список локальных переменных и аргументов, передавая `IDebugProperty2::EnumChildren` `guidFilter` аргумент `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` вызовы [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) и [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), объединение результатов в одного перечисления. См. в разделе [отображение "Локальные"](../../extensibility/debugger/displaying-locals.md) для получения дополнительных сведений.  
  
## <a name="see-also"></a>См. также  
 [Реализация вычислителя выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
