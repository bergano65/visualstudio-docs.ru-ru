---
title: IDebugPort2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725229"
---
# <a name="idebugport2"></a>IDebugPort2
Этот интерфейс представляет собой отладка порта на машине.

## <a name="syntax"></a>Синтаксис

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Поставщик пользовательских портов реализует этот интерфейс, чтобы представлять порт отладки на машине.

 Если порт поддерживает события отправки порта, <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> он должен <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> также реализовать интерфейс для поддержки интерфейса, который, в свою очередь, предоставляет интерфейс [IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 Звонки в [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) или [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) возвращают этот интерфейс, представляя запрашиваемый порт.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPort2`.

|Метод|Описание|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Возвращает название порта.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Возвращает идентификатор порта.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Возвращает запрос, используемый для создания порта (если он доступен).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Возвращает поставщика порта для этого порта.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Возвращает интерфейс в процесс с учетом идентификатора процесса.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Перечисляет все процессы, работающие в порту.|

## <a name="remarks"></a>Примечания
 Местный порт предоставляет доступ ко всем процессам и программам, работающим на локальной машине. Другие порты могут представлять собой последовательное кабельное соединение с устройством на базе Windows CE или сетевое подключение к компьютеру, не относящемуся к DCOM. Интерфейс `IDebugPort2` используется для поиска имени и идентификатора порта и перечисляет все процессы, работающие в порту. В `IDebugPortEx2` интерфейсе внедряются средства для запуска и прекращения процессов в порту.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
