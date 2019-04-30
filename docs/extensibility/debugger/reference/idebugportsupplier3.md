---
title: IDebugPortSupplier3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca7113a1b108713b5dd7cf0f17511cec39a1b8b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918001"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Этот интерфейс позволяет вызывающему объекту определить ли поставщика порта можно сохранить порты (путем их записи на диск) между вызовами отладчика, а затем получите список сохраненных порты.

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский порт поставщик реализует этот интерфейс для поддержки сохранения или сохранить сведения о портах на диск. Этот интерфейс должен быть реализован на один и тот же объект как [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugPortSupplier2` интерфейс для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, наследуемых от [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) интерфейс, этот интерфейс поддерживает следующие:

|Метод|Описание|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Возвращает ли поставщика порта может сохранять данные порты (при их записи на диск) между вызовами отладчика.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Возвращает объект, который может использоваться для перечисления через все порты, которые были записаны на диск, этот поставщик порта.|

## <a name="remarks"></a>Примечания
 Если поставщик порта можно сохранять порты между вызовами, он должен реализовывать этот интерфейс. Порты должны быть загружены при создании экземпляра поставщика порта и записываются на диск при уничтожении поставщика порта.

 Модуль отладки обычно не взаимодействует с поставщика порта и не понадобится для данного интерфейса.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)