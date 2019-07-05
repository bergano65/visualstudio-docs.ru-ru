---
title: IDebugCoreServer3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9a8e6e16aa9279bb7324f5d08f0da3035f2b85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343998"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Этот интерфейс предоставляет доступ к информации о сервере, в которой выполняется процесс.

## <a name="syntax"></a>Синтаксис

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Visual Studio реализует этот интерфейс.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Используйте [QueryInterface](/cpp/atl/queryinterface) для получения этого интерфейса из [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс. Вызов [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) также может возвращать этот интерфейс. Этот интерфейс используется чаще всего поставщика пользовательского порта для запуска программ на сервере (локальных или удаленных).

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейс, этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Извлекает имя сервера.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Извлекает понятная версия имени сервера|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Сообщает о конкретных отладчиков, чтобы автоматически подключиться к процессам, при запуске этих процессов.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Возвращает конкретный код ошибки, если автоматическое присоединение завершается с ошибкой.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Создает экземпляр модуля отладки на сервере.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Получает флаг, указывающий, является ли сервер на том же компьютере, что и вызывающий объект.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Получает значение, указывающее протокол, используемый для связи с сервером.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Отключает все автоприсоединение параметры для всех обработчиков отладки, этот сервер знает.|

## <a name="remarks"></a>Примечания
 Получает поставщика пользовательского порта [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) интерфейса во время вызова [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md). `IDebugCoreServer3` Интерфейса можно получить из этого интерфейса.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)