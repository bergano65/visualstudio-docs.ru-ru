---
title: IDebugManagedПредмет (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject
helpviewer_keywords:
- IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fbd270aa1b65f05f308d41d22f154fb53b8833d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727692"
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс позволяет оценщику выражения (EE) вызывать свойства или методы `System.Decimal`на экземплярах класса значений (например, ) и устанавливать их значение без вызова [Оценка](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) отладки программы.

## <a name="syntax"></a>Синтаксис

```
IDebugManagedObject : IDebugObject
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс для представления управляемого объекта кода, такого как переменная.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Чтобы получить этот интерфейс, позвоните [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) на [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) который представляет собой экземпляр класса значений.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам, унаследованных `IDebugManagedObject` от [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md)интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Возвращает интерфейс, представляющий управляемый объект кода и из которого можно получить любой соответствующий управляемый интерфейс кода.|
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Устанавливает значение этого объекта к значению указанного управляемого объекта кода.|

## <a name="remarks"></a>Примечания
 Оценщик выражения использует этот интерфейс для хранения управляемого объекта кода в дереве разбора.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Оценка](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)
