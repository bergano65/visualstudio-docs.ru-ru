---
title: IDiaLoadCallback | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 353e7dcbe1bcc44b9e8b7e9c7c417913ef07be35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828410"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Получает обратные вызовы из символа доступа к интерфейсу отладки, поиск процедуры, что позволяет пользовательский интерфейс для отчета о ходе попытки расположение.

## <a name="syntax"></a>Синтаксис

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Следующие методы предоставляемые этим интерфейсом:

|Метод|Описание|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Вызывается, когда был найден каталог отладки в файл .exe.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Вызывается, когда был открыт файл .dbg кандидатов.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Вызывается, когда кандидат PDB-файл был открыт.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Определяет, если запросы реестра могут использоваться для поиска пути поиска символов.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Определяет, если доступ разрешен на сервере символов для разрешения символов.|

## <a name="remarks"></a>Примечания
 Клиентское приложение реализует этот интерфейс и предоставляет ссылку на него в вызове [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.

 Дополнительные ограничения, которые могут быть наложены на процесс загрузки, см. в разделе [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: dia2.h

 Библиотека: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)