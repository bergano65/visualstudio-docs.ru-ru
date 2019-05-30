---
title: Изменение значения локальной переменной | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 998200420cf2ec5e0b021a415cdb9d287b1362db
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349758"
---
# <a name="change-the-value-of-a-local"></a>Изменение значения локальной переменной
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Когда вводится новое значение в поле значения **"Локальные"** окна, размер пакета отладки передает строку, как ввели средству оценки выражений (EE). EE оценивает это строка, которая может содержать простое значение или выражение и сохраняет полученное значение в связанной локальной.

 Это Обзор процесса изменения значения локальной переменной:

1. После того как пользователь введет новое значение, Visual Studio вызывает [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) на [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, связанный с локальной.

2. Метод `IDebugProperty2::SetValueAsString` выполняет указанные ниже задачи.

   1. Оценивает строку для получения значения.

   2. Привязывает связанный [IDebugField](../../extensibility/debugger/reference/idebugfield.md) объекта, чтобы получить [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) объекта.

   3. Преобразует значение в последовательность байтов.

   4. Вызовы [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) расшифровка значения байтов памяти, поэтому отлаживаемой программы можно получить доступ к их.

3. Visual Studio обновляет **"Локальные"** отображения (см. в разделе ["Локальные" Отображение](../../extensibility/debugger/displaying-locals.md) сведения).

   Эта процедура также используется для изменения значения переменной в **Watch** окна, но является `IDebugProperty2` объект, связанный со значением локальная переменная, используется вместо `IDebugProperty2` объект, связанный с локальной сам.

## <a name="in-this-section"></a>Содержание раздела
 [Пример реализации изменяющихся значений](../../extensibility/debugger/sample-implementation-of-changing-values.md) использует выборку MyCEE для пошаговое описание процесса изменения значений.

## <a name="see-also"></a>См. также
- [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)