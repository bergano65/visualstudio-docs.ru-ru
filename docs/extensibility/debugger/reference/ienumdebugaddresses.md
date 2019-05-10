---
title: IEnumDebugAddresses | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 261c40fcabf9d5fe3fa99e89a43734bb8f9f245c
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223313"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Этот интерфейс представляет коллекцию объектов, реализующая [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиком символ для предоставления наборы объектов, реализующих [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) интерфейс. Обратите внимание, что это не стандартные перечисление COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) метод.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс возвращается [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) и [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Извлекает следующий набор [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объекты из перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Пропускает заданное число позиций.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Сбрасывает перечисление к первой записи.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Возвращает число элементов перечисления.|

## <a name="remarks"></a>Примечания
 Этот интерфейс обычно используется ядром отладки, чтобы определить соответствующий адрес, чтобы предоставить средству оценки выражений.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)