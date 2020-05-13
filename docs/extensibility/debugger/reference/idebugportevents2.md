---
title: IDebugPortEvents2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c611eb531bdabb633b11ac2e8ca2d0d11f52005
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725175"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
Этот интерфейс уведомляет слушателя (обычно диспетчера отладки сеанса (SDM) или движок отладки) о создании и уничтожении программы в определенном порту. Эта информация может быть использована для представления в режиме реального времени представления процессов и программ, работающих в порту.

## <a name="syntax"></a>Синтаксис

```
IDebugPortEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Visual Studio обычно реализует этот интерфейс для получения уведомлений о создании и уничтожении программы. Отладка двигателя может также реализовать этот интерфейс для прослушивания таких событий порта.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Все интерфейсы [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) могут быть <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> запрошены для интерфейса. Затем <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> метод `IDebugPortEvents2` для называется <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> в интерфейсе, чтобы получить <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс. Наконец, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метод <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> в интерфейсе вызывается для отправки событий через метод [События.](../../../extensibility/debugger/reference/idebugportevents2-event.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице `IDebugPortEvents2`показан метод .

|Метод|Описание|
|------------|-----------------|
|[Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Отправляет события, описывающие создание и разрушение процессов и программ в порту.|

## <a name="remarks"></a>Примечания
 `IDebugPortEvents2`также используется SDM для отладки программ, которые работают в процессе, который уже отлажен.

 События порта передаются в SDM этим интерфейсом.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
