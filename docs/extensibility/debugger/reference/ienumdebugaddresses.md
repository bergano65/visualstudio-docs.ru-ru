---
title: IEnumDebugАдреса Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717582"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
Этот интерфейс представляет собой набор объектов, реализующих интерфейс [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="syntax"></a>Синтаксис

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован поставщиком символов для предоставления наборов объектов, реализующих интерфейс [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md) Обратите внимание, что это не стандартный пересчет COM из-за присутствия метода [GetCount.](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс возвращается [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) и [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Извлекает следующий набор объектов [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) из перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Пропускает определенное количество записей.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Сброс исчисляется перечислением первой записи.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md) (Клонировать)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Извлекает количество записей в перечислении.|

## <a name="remarks"></a>Примечания
 Этот интерфейс обычно используется движком отладки, чтобы помочь определить подходящий адрес, чтобы дать оценщику выражения.

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
