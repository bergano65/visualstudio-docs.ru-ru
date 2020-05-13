---
title: IDebugObject2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726073"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> В Visual Studio 2015 этот способ внедрения оценщиков экспресс-выражений унижается. Для получения информации о реализации оценщиков экспрессии CLR, пожалуйста, ознакомьтесь с [clR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [образцом управляемого оценщика экспрессии.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Этот интерфейс предоставляет дополнительную информацию об объекте.

## <a name="syntax"></a>Синтаксис

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Оценщик выражения реализует этот интерфейс, чтобы предложить поддержку псевдонимов и доступ к информации об объекте.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Интерфейс [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) может получить этот интерфейс с помощью [queryInterface.](/cpp/atl/queryinterface) Кроме того, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) возвращает этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 В дополнение к методам на интерфейсе [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) `IDebugObject2` интерфейс реализует следующие:

|Метод|Описание|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Получает поле или переменную (если таковая имеется), которая может поддерживать свойство, представленное этим объектом.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Получает управляемый объект кода, представляющий значение этого объекта.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Создает уникальный идентификатор для этого объекта или возвращает существующий псевдоним.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Получает псевдоним, связанный с этим объектом, если таковые имеется.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Получает тип этого объекта.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Определяет, представляет ли этот объект данные пользователей.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Определяет, является ли состояние Edit and Continue недействительным.<br /><br /> Пользовательский оценщик выражения не реализует этот `E_NOTIMPL`метод (он должен всегда возвращаться).|

## <a name="remarks"></a>Примечания
 Смотрите [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) для обсуждения псевдонимов.

## <a name="requirements"></a>Требования
 Заголовок: ee.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы вычисления выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [Getobject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
