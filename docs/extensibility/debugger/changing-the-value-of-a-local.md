---
title: Изменение значения локального объекта | Документация Майкрософт
description: Сведения о процессе изменения значения локального объекта при вводе нового значения в поле значение окна Локальные.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f11be641cb77b6b27b735b7a4f66d45e11d7a193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930685"
---
# <a name="change-the-value-of-a-local"></a>Изменение значения локального
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Когда в поле значение окна " **локальные** " вводится новое значение, пакет отладки передает строку как типизированную в средство оценки выражений (EE). EE вычисляет эту строку, которая может содержать либо простое значение, либо выражение, и сохраняет полученное значение в связанном локальном объекте.

 Это обзор процесса изменения значения локального:

1. После того, как пользователь введет новое значение, Visual Studio вызывает [сетвалуеасстринг](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) для объекта [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , связанного с локальным объектом.

2. `IDebugProperty2::SetValueAsString` выполняет следующие задачи:

   1. Вычисляет строку для получения значения.

   2. Привязывает связанный объект [идебугфиелд](../../extensibility/debugger/reference/idebugfield.md) для получения объекта [идебугобжект](../../extensibility/debugger/reference/idebugobject.md) .

   3. Преобразует значение в последовательность байтов.

   4. Вызывает [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) для помещения байтов значения в память, чтобы отлаживаемая программа могла получить к ним доступ.

3. Visual Studio обновляет отображение **локальных переменных** (Дополнительные сведения см. в разделе [отображение локальных переменных](../../extensibility/debugger/displaying-locals.md) ).

   Эта процедура также используется для изменения значения переменной в окне **контрольных** значений, за исключением того, что это `IDebugProperty2` объект, связанный со значением локального объекта, который используется вместо `IDebugProperty2` объекта, связанного с локальным.

## <a name="in-this-section"></a>Содержание раздела
 [Пример реализации изменяемых значений](../../extensibility/debugger/sample-implementation-of-changing-values.md) Использует пример Мицее для пошагового выполнения процесса изменения значений.

## <a name="see-also"></a>См. также раздел
- [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
