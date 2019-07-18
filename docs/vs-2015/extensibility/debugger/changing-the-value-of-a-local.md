---
title: Изменение значения локальной переменной | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383458"
---
# <a name="changing-the-value-of-a-local"></a>Изменение значения локальной переменной
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Когда вводится новое значение в поле значения **"Локальные"** окна, размер пакета отладки передает строку, как ввели средству оценки выражений (EE). EE оценивает это строка, которая может содержать простое значение или выражение и сохраняет полученное значение в связанной локальной.  
  
 Это Обзор процесса изменения значения локальной переменной:  
  
1. После того как пользователь введет новое значение, Visual Studio вызывает [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) на [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, связанный с локальной.  
  
2. Метод `IDebugProperty2::SetValueAsString` выполняет указанные ниже задачи.  
  
   1. Оценивает строку для получения значения.  
  
   2. Привязывает связанный [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, чтобы получить [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта.  
  
   3. Преобразует значение в последовательность байтов.  
  
   4. Вызовы [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) расшифровка значения байтов памяти, поэтому отлаживаемой программы можно получить доступ к их.  
  
3. Visual Studio обновляет **"Локальные"** отображения (см. в разделе [отображение "Локальные"](../../extensibility/debugger/displaying-locals.md) сведения).  
  
   Эта процедура также используется для изменения значения переменной в **Watch** окно тем исключением, что `IDebugProperty2` объект, связанный со значением локальная переменная, используется вместо `IDebugProperty2` объект, связанный с локальной сам.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Пример реализации изменяющихся значений](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Использует образец MyCEE для пошаговое описание процесса изменения значений.  
  
## <a name="see-also"></a>См. также  
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
