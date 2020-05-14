---
title: Отображение Местных жителей (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738927"
---
# <a name="display-locals"></a>Отображение местных жителей
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Выполнение всегда происходит в контексте метода, также известного как содержащий метод или текущий метод. Когда выполнение приостанавливается, Visual Studio вызывает движок отладки (DE), чтобы получить список локальных переменных и аргументов, коллективно называемых местными жителями метода. Visual Studio отображает этих местных жителей и их ценности в окне **Locals.**

 Для отображения местных жителей DE называет метод [GetMethodProperty,](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) принадлежащий EE, и дает ему контекст оценки, то есть поставщика символов (SP), текущий адрес выполнения и объект связующего. Для получения дополнительной информации [см.](../../extensibility/debugger/evaluation-context.md) Если вызов выполнен успешно, `IDebugExpressionEvaluator::GetMethodProperty` метод возвращает объект [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) представляющий метод, содержащий текущий адрес выполнения.

 DE призывает [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) получить объект [IEnumDebugPropertyInfo2,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) который фильтруется, чтобы вернуть только местных жителей и перечисляется для создания списка [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) структур. Каждая структура содержит имя, тип и значение локального. Тип и значение хранятся в виде отформатированных строк, пригодных для отображения. Имя, тип и значение обычно отображаются вместе в одной строке окна **Locals.**

> [!NOTE]
> Окна **«Быстрый смотреть»** и **«Смотреть»** также отображают переменные с одинаковым форматом имени, значения и типа. Тем не менее, эти значения получены по `IDebugProperty2::EnumChildren`телефону [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) вместо .

## <a name="in-this-section"></a>В этом разделе
 [Пример реализации местных жителей](../../extensibility/debugger/sample-implementation-of-locals.md) Использует примеры, чтобы пройти через процесс внедрения местных жителей.

## <a name="related-sections"></a>См. также
 [Контекст оценки](../../extensibility/debugger/evaluation-context.md) Объясняет, что, когда движок отладки (DE) вызывает оценщика выражения (EE), он передает три аргумента.

## <a name="see-also"></a>См. также
 [Написать оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
