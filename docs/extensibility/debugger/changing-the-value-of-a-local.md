---
title: Изменение ценности локального (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739145"
---
# <a name="change-the-value-of-a-local"></a>Изменение значения локального
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [оценщиками экспресс-оценщиков CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [выборкой управляемого оценщика](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)экспрессий.

 При вводе нового значения в поле значения окна **Locals** пакет отладки передает строку, как набрано, оценщику выражения (EE). EE оценивает эту строку, которая может содержать как простое значение, либо выражение, и сохраняет полученное значение в связанном локальном значении.

 Это обзор процесса изменения значения локального:

1. После того, как пользователь вводит новое значение, Visual Studio вызывает [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) на [объектI IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) связанный с локальным.

2. `IDebugProperty2::SetValueAsString` выполняет следующие задачи:

   1. Оценивает строку для создания значения.

   2. Связывает связанный объект [IDebugField](../../extensibility/debugger/reference/idebugfield.md) для получения объекта [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md)

   3. Преобразует значение в ряд байтов.

   4. Вызовы [SetValue,](../../extensibility/debugger/reference/idebugobject-setvalue.md) чтобы поместить байты значения в память, чтобы отладка программы мог получить к ним доступ.

3. Visual Studio обновляет дисплей **Locals** (см. [Отображение местных жителей](../../extensibility/debugger/displaying-locals.md) для деталей).

   Эта процедура также используется для изменения значения переменной в окне `IDebugProperty2` **Watch,** за исключением того, что `IDebugProperty2` это объект, связанный со значением локального, который используется вместо объекта, связанного с самим локальным.

## <a name="in-this-section"></a>В этом разделе
 [Пример реализации изменяющихся значений](../../extensibility/debugger/sample-implementation-of-changing-values.md) Использует образец MyCEE для прохождения процесса изменения значений.

## <a name="see-also"></a>См. также
- [Написание оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Отображение местных жителей](../../extensibility/debugger/displaying-locals.md)
