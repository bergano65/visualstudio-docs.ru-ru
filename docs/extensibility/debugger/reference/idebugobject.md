---
title: IDebugObject Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726313"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс представляет собой объект, который создает связующий объект для инкапсулировать значения символов и выражений.

## <a name="syntax"></a>Синтаксис

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс для представления объекта.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс является базовым классом для всех объектов, которые оценщик выражения использует в разогнанных выражениях. Он возвращается по вызову к методу [Bind.](../../../extensibility/debugger/reference/idebugbinder-bind.md) [QueryInterface](/cpp/atl/queryinterface) получает более специализированные интерфейсы из этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugObject`.

|Метод|Описание|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Получает размер объекта.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Получает значение объекта в виде последовательной серии байтов.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Устанавливает значение объекта из последовательной серии байтов.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Устанавливает эталонное значение этого объекта.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Получает контекст памяти, представляющий адрес значения объекта.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Создает копию управляемого объекта в адресном пространстве движка отладки.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Проверяет, является ли этот объект нулевой ссылкой.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Сравнивает объект с этим.|
|[Isreadonly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Определяет, является ли этот объект прочитан только для чтения.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Определяет, является ли объект прозрачным прокси.|

## <a name="remarks"></a>Примечания
 Оценщик выражения использует этот интерфейс в качестве базового класса для представления объектов в дереве разбора.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)
