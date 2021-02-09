---
title: Стратегия реализации средства оценки выражений | Документация Майкрософт
description: Сведения о стратегии создания вычислительных выражений путем первой реализации кода для вывода локальных переменных в окне Локальные.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7527c361a889d5aa1f19ec7a211f8aeb8dcbd15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921384"
---
# <a name="expression-evaluator-implementation-strategy"></a>Стратегия реализации средства оценки выражений
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Один из подходов к быстрому созданию средства оценки выражений (EE) заключается в том, чтобы сначала реализовать минимальный код, необходимый для вывода локальных переменных в окне **локальные** . Полезно понимать, что каждая строка в окне **локальные** отображает имя, тип и значение локальной переменной, а все три представляются объектом [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Имя, тип и значение локальной переменной получаются из `IDebugProperty2` объекта путем вызова его метода [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Дополнительные сведения о том, как отображать локальные переменные в окне **локальные** , см. в разделе [отображение локальных](../../extensibility/debugger/displaying-locals.md)переменных.

## <a name="discussion"></a>Разговор
 Возможная последовательность реализации начинается с реализации [идебужекспрессионевалуатор](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Для вывода локальных переменных должны быть реализованы методы [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) и [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) . Вызов `IDebugExpressionEvaluator::GetMethodProperty` возвращает `IDebugProperty2` объект, представляющий метод:, то есть объект [идебугмесодфиелд](../../extensibility/debugger/reference/idebugmethodfield.md) . Сами методы не отображаются в окне **локальные** .

 Метод [енумчилдрен](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) должен быть реализован далее. Модуль отладки (DE) вызывает этот метод для получения списка локальных переменных и аргументов путем передачи `IDebugProperty2::EnumChildren` `guidFilter` аргумента `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` вызывает [енумаргументс](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) и [енумлокалс](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), объединяя результаты в одно перечисление. Дополнительные сведения см. в разделе [отображение локальных переменных](../../extensibility/debugger/displaying-locals.md) .

## <a name="see-also"></a>См. также раздел
- [Реализация средства оценки выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [Отобразить локальные переменные](../../extensibility/debugger/displaying-locals.md)
