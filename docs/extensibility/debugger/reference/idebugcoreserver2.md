---
title: IDebugCoreServer2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f4f01bb8e86e733bef3940a4772f52b28080628
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712389"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Этот интерфейс используется для представления и получения сведений с сервера на компьютере в сети.

## <a name="syntax"></a>Синтаксис

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс для представления сервера. Каждый экземпляр Visual Studio создает экземпляр этого интерфейса.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Пользовательский порт поставщика получает этот интерфейс в вызове [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Модуль отладки можно получить этот интерфейс косвенно посредством вызова [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (который возвращает [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), интерфейс, который является производным от `IDebugCoreServer2`).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugCoreServer2`.

|Метод|Описание|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Получает имя и атрибуты машины.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Возвращает имя машины.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Получает поставщика порта, который существует на компьютере.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Получает порт, который уже существует на компьютере.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Создает перечислитель для всех портов на компьютере.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Создает перечислитель для всех поставщиков, порт на компьютере.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Получает служебные программы машины для машины.|

## <a name="remarks"></a>Примечания
 Этот интерфейс также используется в Visual Studio для просмотра процессов, запущенных на компьютерах в сети.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)