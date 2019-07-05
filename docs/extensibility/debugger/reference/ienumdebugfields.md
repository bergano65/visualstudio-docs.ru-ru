---
title: IEnumDebugFields | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50d80242ca516c5fa7f3ad297250e25c782664d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350371"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Этот интерфейс представляет коллекцию объектов, реализующая [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиком символ для предоставления наборы объектов, реализующих [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс. Обратите внимание, что это не стандартные перечисление COM из-за наличия [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) метод.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Этот интерфейс возвращается [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) и [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Извлекает следующий набор [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) объекты из перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Пропускает заданное число позиций.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Сбрасывает перечисление к первой записи.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Возвращает число элементов перечисления.|

## <a name="remarks"></a>Примечания

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)