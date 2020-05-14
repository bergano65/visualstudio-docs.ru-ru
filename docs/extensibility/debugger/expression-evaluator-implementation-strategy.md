---
title: Стратегия реализации экспресс-оценки (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738668"
---
# <a name="expression-evaluator-implementation-strategy"></a>Стратегия реализации оценки экспрессии
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Один из подходов к быстрому созданию оценщика выражения (EE) заключается в том, чтобы сначала реализовать минимальный код, необходимый для отображения локальных переменных в окне **Locals.** Полезно понимать, что каждая строка в окне **Locals** отображает имя, тип и значение локальной переменной, и что все три представлены объектом [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md) Имя, тип и значение локальной переменной получены от `IDebugProperty2` объекта, позвонив в метод [GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Для получения дополнительной информации о том, как отображать локальные переменные в окне **Locals,** [см.](../../extensibility/debugger/displaying-locals.md)

## <a name="discussion"></a>Обсуждение
 Возможная последовательность реализации начинается с реализации [IDebugExpressionEvaluator.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) [Методы Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) и [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) должны быть реализованы для отображения местных жителей. Вызов `IDebugExpressionEvaluator::GetMethodProperty` возвращает `IDebugProperty2` объект, представляющий метод, то есть объект [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) Сами методы не отображаются в окне **Locals.**

 Следующий метод [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) должен быть реализован. Отладка двигателя (DE) вызывает этот метод, чтобы получить список `IDebugProperty2::EnumChildren` `guidFilter` локальных `guidFilterLocalsPlusArgs`переменных и аргументов, передавая аргумент . `IDebugProperty2::EnumChildren`звонки [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) и [EnumLocals,](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)комбинируя результаты в одном перечислении. Более подробную информацию можно узнать из [местных жителей.](../../extensibility/debugger/displaying-locals.md)

## <a name="see-also"></a>См. также
- [Реализация оценщика выражения](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Отображение местных жителей](../../extensibility/debugger/displaying-locals.md)
