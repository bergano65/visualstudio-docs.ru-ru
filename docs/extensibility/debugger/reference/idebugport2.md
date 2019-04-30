---
title: IDebugPort2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14c21b4f1546b262fb61c0da3ea95adee2aef8fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918286"
---
# <a name="idebugport2"></a>IDebugPort2
Этот интерфейс представляет порт отладки на компьютере.

## <a name="syntax"></a>Синтаксис

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Пользовательский порт поставщик реализует этот интерфейс для представления порта отладки на компьютере.

 Если порт поддерживает отправку событий порт, он также должен реализовать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс для поддержки <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс, который в свою очередь обеспечивает [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовы [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) или [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) возвращать этот интерфейс, представляющий запрошенный порт.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPort2`.

|Метод|Описание|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Возвращает имя порта.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Возвращает идентификатор порта.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Возвращает запрос, используемый для создания порта (если доступно).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Возвращает поставщика порта для этого порта.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Возвращает интерфейс к процессу, заданному идентификатором процесса.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Перечисляет все процессы, работающие на порте.|

## <a name="remarks"></a>Примечания
 Локальный порт предоставляет доступ ко всем процессам и программы, запущенные на локальном компьютере. Другим портам, может представлять последовательный кабель подключение устройства на базе Windows CE или сетевое подключение к компьютеру без DCOM. `IDebugPort2` Интерфейс используется для поиска имя и идентификатор порта и перечислить все процессы, запущенные на порт. Средства для запуска и завершения процессов в порт, реализуются в `IDebugPortEx2` интерфейс.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)