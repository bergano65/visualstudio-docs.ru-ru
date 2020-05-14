---
title: Контекст оценки (англ.) Документы Майкрософт
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
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738799"
---
# <a name="evaluation-context"></a>Контекст оценки
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)CLR [см.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

 Когда движок отладки (DE) вызывает оценщика выражения (EE), три аргумента, которые передаются [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) определяют контекст для поиска и оценки символов, как показано в следующей таблице.

## <a name="arguments"></a>Аргументы

|Аргумент|Описание|
|--------------|-----------------|
|`pSymbolProvider`|Интерфейс [IDebugSymbolProvider,](../../extensibility/debugger/reference/idebugsymbolprovider.md) который определяет обработчик символов (SH), который будет использоваться для идентификации символа.|
|`pAddress`|Интерфейс [IDebugAddress,](../../extensibility/debugger/reference/idebugaddress.md) который определяет текущую точку выполнения. Этот интерфейс находит метод, содержащий выполняемый код.|
|`pBinder`|[Интерфейс IDebugBinder,](../../extensibility/debugger/reference/idebugbinder.md) который находит значение и тип символа, данного его имени.|

 `IDebugParsedExpression::EvaluateSync`возвращает интерфейс [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) представляющий полученное значение и его тип.

## <a name="see-also"></a>См. также
- [Интерфейсы оценщика ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Отображение местных жителей](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
