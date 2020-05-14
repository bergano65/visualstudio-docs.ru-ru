---
title: IDebugPortSupplier3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724436"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Этот интерфейс позволяет вызывающему определить, может ли поставщик портов сохранять порты (написав их на диск) между вызовами отладчика, а затем получить список сохраненных портов.

## <a name="syntax"></a>Синтаксис

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик пользовательских портов реализует этот интерфейс для поддержки сохраняющейся или сохранения портовой информации на диске. Этот интерфейс должен быть реализован на том же объекте, что и интерфейс [IDebugPortSupplier2.](../../../extensibility/debugger/reference/idebugportsupplier2.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 Вызов [queryInterface](/cpp/atl/queryinterface) `IDebugPortSupplier2` на интерфейс, чтобы получить этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
 В дополнение к методам, унаследованных от интерфейса [IDebugPortSupplier2,](../../../extensibility/debugger/reference/idebugportsupplier2.md) этот интерфейс поддерживает следующее:

|Метод|Описание|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Возвращает вопрос о том, может ли поставщик порта сохранять порты (написав их на диск) между вызовами отладчика.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Возвращает объект, который можно использовать для перечисления через все порты, которые были написаны на диску этим поставщиком порта.|

## <a name="remarks"></a>Примечания
 Если поставщик портов может сохранять порты через вызовы, он должен реализовать этот интерфейс. Порты должны быть загружены, когда поставщик порта мгновенно, и записаны на диск, когда поставщик порта уничтожен.

 Двигатель отладки обычно не взаимодействует с поставщиком порта и не будет использовать этот интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
