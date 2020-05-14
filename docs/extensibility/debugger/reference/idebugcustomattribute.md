---
title: IDebugCustomАтрибут (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732675"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
Этот интерфейс представляет собой пользовательский атрибут и может предоставить тип имени, родительских и классов.

## <a name="syntax"></a>Синтаксис

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс для поддержки пользовательских атрибутов, связанных с символом. Как правило, он реализуется на своем собственном объекте.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [в Следующую](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) возвращает этот интерфейс. Вызов в метод [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает интерфейс [IEnumDebugCustomAttributes.](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugCustomAttribute`.

|Метод|Описание|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Получает поле, к которому прикрепляется текущий атрибут.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Получает пользовательский тип класса атрибутов.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Получает название пользовательского атрибута.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Получает информацию о атрибутах в виде капли байтов.|

## <a name="remarks"></a>Примечания
 Пользовательский атрибут — это структура для C, которая поставляет пользовательские метаданные, связанные с определенным классом или методом.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
