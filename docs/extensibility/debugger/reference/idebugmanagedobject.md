---
title: IDebugManagedObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 295e1829f51ff983e66c11e8f2ae2e5886ee7741
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707980"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  В Visual Studio 2015 таким образом, реализации вычислители выражений является устаревшим. Сведения о реализации вычислители выражений CLR, см. в разделе [вычислители выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [управляемых образец средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Этот интерфейс позволяет вычислитель выражений (EE) для вызова свойства или методы в экземплярах класса значение (например, `System.Decimal`) и задать их без вызова [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) на отлаживаемой программы.

## <a name="syntax"></a>Синтаксис

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Вычислитель выражений реализует этот интерфейс представляет объект управляемого кода, такие как переменная.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Чтобы получить этот интерфейс, вызовите [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) на [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , представляющий экземпляр класса значений.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, наследуемых от [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), `IDebugManagedObject` интерфейс предоставляет следующие методы.

|Метод|Описание:|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Возвращает интерфейс, представляющий объект управляемого кода и из какой любой соответствующий управляемый код может быть получен интерфейс.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Задает значение этого объекта к значению объекта указанный управляемый код.|

## <a name="remarks"></a>Примечания
 Вычислитель выражений использует этот интерфейс, чтобы сохранить объект управляемого кода в дерево синтаксического анализа.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)