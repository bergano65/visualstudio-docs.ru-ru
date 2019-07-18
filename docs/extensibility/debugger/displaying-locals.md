---
title: Отображение локальных переменных | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a8a73fb8ab95602538be56f18834233dbad7132
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345789"
---
# <a name="display-locals"></a>Отображение локальных переменных
> [!IMPORTANT]
> В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образец средства оценки выражений управляемый](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Выполнение всегда выполняется в контексте метода, также известный как содержащего метода или текущий метод. Когда выполнение приостанавливается, Visual Studio вызывает модуль отладки (DE), чтобы получить список локальных переменных и аргументов, которые в совокупности называются локальные переменные метода. Visual Studio отображает эти локальные переменные и их значения в **"Локальные"** окна.

 Чтобы отобразить "Локальные", вызывает DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) метода, принадлежащего объекту EE и присваивает ему контекст вычисления, который является, поставщика символов (SP), текущий адрес выполнения и объект связывателя. Дополнительные сведения см. в разделе [контекст оценки](../../extensibility/debugger/evaluation-context.md). Если вызов завершается успешно, `IDebugExpressionEvaluator::GetMethodProperty` возвращает [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) объект, который представляет метод, который содержит адрес текущего выполнения.

 Вызовы DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) для получения [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) объекта, который является отфильтрованы, чтобы возвращать только локальные переменные и перечислить для создания списка [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)структуры. Каждая структура содержит имя, тип и значения локальной переменной. Тип и значение хранятся в виде форматированных строк, подходящее для отображения. Имя, тип и значение обычно отображаются вместе в одной строке **"Локальные"** окна.

> [!NOTE]
> **"Быстрая проверка"** и **Watch** окнах также отображаются переменные с тот же формат, имя, значение и тип. Тем не менее, эти значения получаются путем вызова [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вместо `IDebugProperty2::EnumChildren`.

## <a name="in-this-section"></a>Содержание раздела
 [Пример реализации локальных переменных](../../extensibility/debugger/sample-implementation-of-locals.md) используются примеры для пошагового выполнения процесс реализации "Локальные".

## <a name="related-sections"></a>Связанные разделы
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) объясняет, что когда модуль отладки (DE) вызывает средство оценки выражений (EE), он передает три аргумента.

## <a name="see-also"></a>См. также
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)