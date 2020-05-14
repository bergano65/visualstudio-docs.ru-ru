---
title: IDebugCoreServer3 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732810"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Этот интерфейс предоставляет доступ к информации о сервере, в который работает процесс.

## <a name="syntax"></a>Синтаксис

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Visual Studio реализует этот интерфейс.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Используйте [queryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из интерфейса [IDebugCoreServer2.](../../../extensibility/debugger/reference/idebugcoreserver2.md) Звонок [в GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) также может вернуть этот интерфейс. Этот интерфейс чаще всего используется поставщиком портов для запуска программ на сервере (локальном или удаленном).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсе [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Извлекает имя сервера.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Получение дружественной версии имени сервера|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Сообщает, что конкретные двигатели отладки автоматически прикрепляются к процессам при запуске этих процессов.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Извлекает определенный код ошибки при сбоях автоматического крепления.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Создает экземпляр отладки двигателя на сервере.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Извлекает флаг, указывающий, находится ли сервер на той же машине, что и абонент.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Извлекает значение, указывающее на протокол, используемый для связи с сервером.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Отклоняет все настройки автоматического присоединения для всех отладок двигателей, о чем знает этот сервер.|

## <a name="remarks"></a>Примечания
 Поставщик пользовательских портов получает интерфейс [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) по вызову [на event.](../../../extensibility/debugger/reference/idebugportevents2-event.md) Интерфейс `IDebugCoreServer3` можно получить из этого интерфейса.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
