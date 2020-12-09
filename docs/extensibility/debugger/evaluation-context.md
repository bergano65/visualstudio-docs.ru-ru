---
title: Контекст оценки | Документация Майкрософт
description: 'Когда модуль отладки вызывает средство оценки выражений, аргументы определяют контекст для поиска и вычисления символов: Псимболпровидер, Паддресс и Пбиндер.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a021d5dfdff5058211f5bafdfd7854611f977c27
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914521"
---
# <a name="evaluation-context"></a>Контекст оценки
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Когда модуль отладки (DE) вызывает средство оценки выражений (EE), три аргумента, передаваемые в [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) , определяют контекст для поиска и вычисления символов, как показано в следующей таблице.

## <a name="arguments"></a>Аргументы

|Аргумент|Описание|
|--------------|-----------------|
|`pSymbolProvider`|Интерфейс [идебугсимболпровидер](../../extensibility/debugger/reference/idebugsymbolprovider.md) , указывающий обработчик символов (SH), используемый для обозначения символа.|
|`pAddress`|Интерфейс [идебугаддресс](../../extensibility/debugger/reference/idebugaddress.md) , указывающий текущую точку выполнения. Этот интерфейс находит метод, содержащий выполняемый код.|
|`pBinder`|Интерфейс [идебугбиндер](../../extensibility/debugger/reference/idebugbinder.md) , который находит значение и тип символа по его имени.|

 `IDebugParsedExpression::EvaluateSync` Возвращает интерфейс [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющий результирующее значение и его тип.

## <a name="see-also"></a>См. также раздел
- [Интерфейсы средства оценки ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
