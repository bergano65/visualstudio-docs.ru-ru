---
title: IDiaLoadCallback2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daf0b48aca06b404824059030052223a8545a6b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839710"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
Получает обратные вызовы из символа доступа к интерфейсу отладки, поиск процедуры, что позволяет ограничения, которые необходимо соблюдать на процесс поиску.

## <a name="syntax"></a>Синтаксис

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам в [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) интерфейс, этот интерфейс предоставляет следующие методы:

|Метод|Описание|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Определяет, если поиск PDB-файл в исходном каталоге отладки.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|Определяет, разрешено при поиске PDB-файл в каталоге, где находится файл .exe.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Определяет, если может найти отладочную информацию из DBG-файлы.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Определяет, разрешено при поиске PDB-файлы в корневом каталоге системы.|

## <a name="remarks"></a>Примечания
 Клиентское приложение реализует этот интерфейс и предоставляет ссылку на него в вызове [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод. Не забудьте реализует все методы в [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) также интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: dia2.h

 Библиотека: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>См. также
- [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)