---
title: "Отображение локальных переменных | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "отладка [отладка SDK], вычисление выражений"
  - "вычисление выражений, отображение локальные переменные"
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Отображение локальных переменных
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Выполнение всегда выполняется в контексте метода, также известные как содержащего метода или текущий метод. Когда выполнение приостанавливается, Visual Studio вызывает отладчик \(DE\), чтобы получить список локальных переменных и аргументов, которые в совокупности называются локальные переменные метода. Visual Studio отображает эти локальные переменные и их значения в **Локальные** окна.  
  
 Чтобы отобразить локальные переменные, вызывает DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) методу, относящемуся к EE и предоставляет контекст вычисления, который является, поставщик символ \(SP\), текущий адрес выполнения и объект привязки. Для получения дополнительной информации см. [Контекст оценки](../../extensibility/debugger/evaluation-context.md). Если вызов завершается успешно, `IDebugExpressionEvaluator::GetMethodProperty` возвращает метод [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, который представляет метод, который содержит адрес текущего выполнения.  
  
 Вызовы DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объекта, который является отфильтрованы, чтобы возвращать только локальные переменные и перечислить для создания списка [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) структуры. Каждая структура содержит имя, тип и значение локального объекта. Тип и значение хранятся в виде форматированных строк, подходящую для отображения. Имя, тип и значение обычно отображаются вместе в одной строке **Локальные** окна.  
  
> [!NOTE]
>  **Быстрая проверка** и **Контрольные значения** windows также отображать переменные с тот же формат, имя, значение и тип. Тем не менее, эти значения получаются путем вызова [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вместо `IDebugProperty2::EnumChildren`.  
  
## В этом подразделе  
 [Пример реализации локальные переменные](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Приводятся примеры проходить через процесс реализации локальные переменные.  
  
## Связанные подразделы  
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md)  
 Объясняет, что когда отладчик \(DE\) вызывает вычислитель выражений \(EE\), передает три аргумента.  
  
## См. также  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)