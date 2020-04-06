---
title: IDebugMethodField Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727061"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
Этот интерфейс описывает метод.

## <a name="syntax"></a>Синтаксис

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс на том же объекте, который реализует интерфейс [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Этот интерфейс представляет собой специализацию, которая представляет метод.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface,](/cpp/atl/queryinterface) чтобы получить этот интерфейс из интерфейса `FIELD_TYPE_METHOD` [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) если [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращается. Кроме того, методы, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), и [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), все вернуть `IDebugMethodField` интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсах [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Создает регистратор параметров метода.|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Получает "этот" указатель объекта, содержащего метод.|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Создает регистратор для всех локальных переменных метода.|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Создает регистратор для отдельных локальных переменных метода.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Определяет, был ли определен определенный атрибут.|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Создает регистратор для статических локальных переменных метода.|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Получает глобальный контейнер метода.|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Создает регистратор для типа каждого аргумента, необходимого для вызова метода.|

## <a name="remarks"></a>Примечания
 Метод может содержать параметры, а также локальные переменные.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
