---
title: IDebugФункцияОбъект (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728499"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс представляет собой функцию.

## <a name="syntax"></a>Синтаксис

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс для представления функции.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс является специализацией интерфейса [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) и получен с `IDebugObject` помощью [queryInterface](/cpp/atl/queryinterface) на интерфейсе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованных `IDebugFunctionObject` от [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md)интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Создает примитивный объект данных.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Создает объект с помощью конструктора.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Создает объект без конструктора.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Создает объект массива.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Создает объект строки.|
|[Оценка](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Вызывает функцию и возвращает полученное значение в качестве объекта.|

## <a name="remarks"></a>Примечания
 Этот интерфейс позволяет оценщику выражения представлять функции в дереве разбора. Методы `Create` этого интерфейса используются для построения объектов, представляющих параметры ввода метода. Функция может быть выполнена путем вызова метода [Оценки,](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) который возвращает объект, представляющий значение возврата функции.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
