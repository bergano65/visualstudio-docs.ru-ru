---
title: IEnumDebugFields Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d577ff2f5848f2cb348bcaccf57875507018634b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716781"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Этот интерфейс представляет собой набор объектов, реализующих интерфейс [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Синтаксис

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован поставщиком символов для предоставления наборов объектов, реализующих интерфейс [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md) Обратите внимание, что это не стандартный пересчет COM из-за присутствия метода [GetCount.](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс возвращается [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) и [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Извлекает следующий набор объектов [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) из перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Пропускает определенное количество записей.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Сброс исчисляется перечислением первой записи.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md) (Клонировать)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Извлекает количество записей в перечислении.|

## <a name="remarks"></a>Примечания

## <a name="requirements"></a>Требования
 Заголовок: sh.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
