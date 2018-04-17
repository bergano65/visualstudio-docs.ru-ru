---
title: Изменение значения локального | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 422d1702f319db6da21892bcaa1bd50adad7909d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="changing-the-value-of-a-local"></a>Изменение значения локального
> [!IMPORTANT]
>  В Visual Studio 2015 этот способ реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 При вводе нового значения в поле значения **локальные** окна, отладочный пакет передает строку, как типизированные вычислитель выражений (EE). EE оценивает этой строки, которая может содержать простое значение или выражение и сохраняет полученное значение в связанной локальной.  
  
 Это общая схема процесса изменения значения локального:  
  
1.  После пользователь вводит новое значение, Visual Studio вызывает [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) на [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, связанный с локальной.  
  
2.  Метод `IDebugProperty2::SetValueAsString` выполняет указанные ниже задачи.  
  
    1.  Оценивает строку для получения значения.  
  
    2.  Привязывает связанный [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, чтобы получить [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта.  
  
    3.  Преобразует значение в последовательность байтов.  
  
    4.  Вызовы [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) перевод значение байтов в памяти, доступ к ним отлаживаемой программы.  
  
3.  Visual Studio обновляет **локальные** отображения (в разделе [отображение локальные](../../extensibility/debugger/displaying-locals.md) подробные сведения).  
  
 Эта процедура также используется для изменения значения переменной в **Контрольные значения** окна, за исключением его `IDebugProperty2` объект, связанный со значением, используемый вместо локальной `IDebugProperty2` объект, связанный с локальным сам.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пример реализации изменяющихся значений](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 В образце MyCEE использует для пошаговый процесс изменения значений.  
  
## <a name="see-also"></a>См. также  
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)