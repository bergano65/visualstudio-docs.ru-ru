---
title: IDebugCustomАтрибутИКери2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732489"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Определяет наличие пользовательского атрибута для этого поля и, если он существует, возвращает информацию атрибута.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс на том же объекте, который реализует [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) для поддержки пользовательских атрибутов.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface,](/cpp/atl/queryinterface) чтобы получить этот интерфейс из интерфейса [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы интерфейса **IDebugCustomAttribute's.**

|Метод|Описание|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Определяет, существует ли пользовательский атрибут по имени.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Получает информацию об атрибуте для данного пользовательского атрибута.|

 В дополнение к методам **IDebugCustomAttribute's,** `IDebugCustomAttributeQuery2` реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Получает регистратор для всех пользовательских атрибутов, прикрепленных к этому полю.|

## <a name="remarks"></a>Примечания
 Метод [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) может вернуть регистратор для всех пользовательских атрибутов, определенных для этого поля.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
