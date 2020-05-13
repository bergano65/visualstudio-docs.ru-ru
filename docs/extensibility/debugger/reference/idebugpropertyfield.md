---
title: IDebugPropertyField Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720697"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
Этот интерфейс предоставляет функции, которые позволяют получить и установить свойство.

## <a name="syntax"></a>Синтаксис

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик символов реализует этот интерфейс на том же объекте, который реализует [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Этот интерфейс является специализацией, которая поддерживает концепцию свойств в классе.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface,](/cpp/atl/queryinterface) чтобы получить этот интерфейс из интерфейса [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) если метод [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) возвращается. `FIELD_KIND_PROP`

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсах [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) и [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Получает метод, который получает свойство.|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Получает метод, который устанавливает свойство.|

## <a name="remarks"></a>Примечания
 Свойство является концепцией управляемого кода и представляет метод, который рассматривается как переменная. Свойства не существуют в неуправляемых СЗ.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
