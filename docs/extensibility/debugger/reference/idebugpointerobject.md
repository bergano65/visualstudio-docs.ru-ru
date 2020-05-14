---
title: IDebugPointerObject (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725487"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс представляет собой объект указателя.

## <a name="syntax"></a>Синтаксис

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс для представления объекта указателя.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Интерфейс [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) может получить этот интерфейс с `IDebugObject` помощью [queryInterface,](/cpp/atl/queryinterface) если представляет собой указатель.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованных `IDebugPointerObject` от [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md)интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|Получает объект, к которому указывает интерфейс.|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|Получает значение, к которому интерфейс указывает в виде серии последовательных байтов.|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|Устанавливает значение, к которому интерфейс указывает из серии последовательных байтов.|

## <a name="remarks"></a>Примечания
 Оценщик выражения использует этот интерфейс для представления указателя в дереве разбора.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
