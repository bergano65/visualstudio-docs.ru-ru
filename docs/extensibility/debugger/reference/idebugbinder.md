---
title: ИдебугБиндер Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735975"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс связывает поле символа, обычно возвращенное поставщиком символов, с контекстом памяти или объектом, содержащим текущее значение символа.

## <a name="syntax"></a>Синтаксис

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс поддерживает оценку выражения и должен быть реализован движком отладки (DE).

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс используется в процессе оценки выражений и обычно используется в реализации [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [EvaluateAsync.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugBinder`.

|Метод|Описание|
|------------|-----------------|
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Получает контекст или объект памяти, содержащий текущее значение символа.|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Определяет тип времени выполнения объекта.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Преобразует местоположение объекта или адрес памяти в контекст памяти.|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Получает объект [IDebugFunctionObject,](../../../extensibility/debugger/reference/idebugfunctionobject.md) используемый для создания параметров функции.|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Получает точный тип для переменной.|

## <a name="remarks"></a>Примечания
 Этот интерфейс возвращает объекты, которые используются оценщиком экспресс-оценщиков в разбирать деревья. Оценщик выражения разбирает выражение, используя поставщика символов для преобразования символов в выражении в экземпляры [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), которые описывают каждый символ с точки зрения его типа и местоположения в исходном коде. Метод [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) преобразует `IDebugField` объекты в объекты [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) которые соединяют или связывают тип символа с фактическим значением в памяти. Эти `IDebugObject` объекты затем хранятся в дереве разбора для последующей оценки.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
