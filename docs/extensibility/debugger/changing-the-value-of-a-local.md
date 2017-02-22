---
title: "Изменение значения локальной | Microsoft Docs"
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
  - "вычисление выражений, программное изменение значения"
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Изменение значения локальной
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 При вводе нового значения в поле значения **Локальные** окне отладочный пакет передает строку, набираемым, вычислитель выражений \(EE\). EE оценивает этой строки, которая может содержать простое значение или выражение и сохраняет полученное значение связанного локальной.  
  
 Это Обзор процесса изменения значения локальной:  
  
1.  После ввода пользователем нового значения, Visual Studio вызывает [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) на [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, связанный с локальной.  
  
2.  `IDebugProperty2::SetValueAsString` выполняет следующие задачи:  
  
    1.  Оценивает строку для получения значения.  
  
    2.  Привязывает связанный [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, чтобы получить [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта.  
  
    3.  Преобразует значение в последовательность байтов.  
  
    4.  Вызовы [SetValue](../Topic/IDebugObject::SetValue.md) поместить значение байтов в памяти, доступ к ним отлаживаемой программы.  
  
3.  Visual Studio обновляет **Локальные** отображения \(в разделе [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md) Подробные сведения\).  
  
 Эта процедура также используется для изменения значения переменной в **Контрольные значения** окна, за исключением его `IDebugProperty2` объект, связанный со значением, используется вместо локальной `IDebugProperty2` объект, связанный с локальной сам.  
  
## Содержание  
 [Пример реализации изменение значений](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Использует образец MyCEE проходить через процесс изменения значений.  
  
## См. также  
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)