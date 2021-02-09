---
title: Идебугфунктионобжект | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab1462c30f1012eb1002f692672fc470cac3b39a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921008"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс представляет функцию.

## <a name="syntax"></a>Синтаксис

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Средство оценки выражений реализует этот интерфейс для представления функции.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс является специализацией интерфейса [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) и получается с помощью [QueryInterface](/cpp/atl/queryinterface) в `IDebugObject` интерфейсе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованным от [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md), `IDebugFunctionObject` интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|Создает примитивный объект данных.|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|Создает объект с помощью конструктора.|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|Создает объект без конструктора.|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|Создает объект Array.|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|Создает строковый объект.|
|[Вычислить](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|Вызывает функцию и возвращает результирующее значение в виде объекта.|

## <a name="remarks"></a>Remarks
 Этот интерфейс позволяет средству оценки выражений представлять функции в дереве синтаксического анализа. `Create`Методы в этом интерфейсе используются для создания объектов, представляющих входные параметры метода. Затем функцию можно выполнить, вызвав метод [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) , который возвращает объект, представляющий возвращаемое значение функции.

## <a name="requirements"></a>Требования
 Заголовок: ee. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
