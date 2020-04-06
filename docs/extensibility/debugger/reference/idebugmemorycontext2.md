---
title: IDebugMemoryКонтекст2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727430"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Этот интерфейс представляет собой положение в адресном пространстве отладки машины.

## <a name="syntax"></a>Синтаксис

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представить адрес в памяти.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Звонок в [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) или [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) возвращает этот интерфейс. Кроме того, после применения соответствующей арифметической операции призывы [добавить](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) и [вычесть](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) новые копии этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugMemoryContext2`.

|Метод|Описание|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Получает имя пользователя для этого контекста.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Получает информацию, описываемую этот контекст.|
|[Добавить](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Добавляет определенное значение к адресу текущего контекста для создания нового контекста.|
|[Вычесть](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Вычитает определенное значение из адреса текущего контекста для создания нового контекста.|
|[Сравнить](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Сравнивает два контекста в порядке, указанном сравните флаги.|

## <a name="remarks"></a>Примечания
 Окно **памяти** Visual Studio вызывает [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) для получения `IDebugMemoryContext2` интерфейса, содержащего оцененное выражение, используемое для адреса памяти. Затем этот контекст передается [в ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) и [WriteAt,](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) чтобы указать адрес для чтения или записи.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
