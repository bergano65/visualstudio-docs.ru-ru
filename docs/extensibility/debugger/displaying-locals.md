---
title: "Отображение локальных переменных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a00d57b8af1c32c2f94334e2930e8f92b166c89b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-locals"></a>Отображение локальных переменных
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Выполнение всегда выполняется в контексте текущего метода или метода, также известные как содержащий метод. Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE), чтобы получить список локальных переменных и аргументов, которые в совокупности называются локальные переменные метода. Visual Studio отображает эти локальные переменные и их значения в **локальные** окна.  
  
 Чтобы отобразить локальные переменные, вызывает DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) метод, принадлежащий EE и присваивает ему контекст вычисления, который является, поставщик символ (SP), текущий адрес выполнения и объект связывателя. Дополнительные сведения см. в разделе [контекст оценки](../../extensibility/debugger/evaluation-context.md). Если вызов завершается успешно, `IDebugExpressionEvaluator::GetMethodProperty` возвращает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, который представляет метод, который содержит адрес текущего выполнения.  
  
 Вызовы DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объекта, который является отфильтрованы, чтобы возвращать только локальные переменные и перечислено для получения списка [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)структуры. Каждая структура содержит имя, тип и значение локального. Тип и значение хранятся в виде форматированных строк, удобному для отображения. Имя, тип и значение обычно отображаются вместе в одной строке **локальные** окна.  
  
> [!NOTE]
>  **Быстрая проверка** и **Контрольные значения** окнах также отображаются переменные с тот же формат, имя, значение и тип. Однако эти значения можно получить путем вызова [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вместо `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>Содержание  
 [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Для пошагового выполнения процесс реализации локальные переменные используются примеры.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Объясняется, когда модуль отладки (DE) вызывает вычислитель выражений (EE), он передает три аргумента.  
  
## <a name="see-also"></a>См. также  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)