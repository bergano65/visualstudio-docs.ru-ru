---
title: Функция Сккпопулатедирлист | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f13c674e6374e826dc45343e5cd1f7edcc1f8100
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720898"
---
# <a name="sccpopulatedirlist-function"></a>Функция SccPopulateDirList
Эта функция определяет, какие каталоги и (при необходимости) файлы хранятся в системе управления версиями с учетом списка каталогов для проверки.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccPopulateDirList(
   LPVOID        pContext,
   LONG          nDirs,
   LPCSTR*       lpDirPaths,
   POPDIRLISTFUNCpfnPopulate,
   LPVOID        pvCallerData,
   LONG          fOptions
);
```

#### <a name="parameters"></a>Параметры
 пконтекст

окне Указатель контекста для подключаемого модуля системы управления версиями.

 ндирс

окне Число путей к каталогу в массиве `lpDirPaths`.

 лпдирпасс

окне Массив путей к каталогу для проверки.

 пфнпопулате

окне Функция обратного вызова для вызова для каждого пути к каталогу и (необязательно) имя файла в `lpDirPaths` (Дополнительные сведения см. в [попдирлистфунк](../extensibility/popdirlistfunc.md) ).

 пвкаллердата

окне Значение, которое должно быть передано в функцию обратного вызова без изменений.

 фоптионс

окне Сочетание значений, управляющих обработкой каталогов (см. раздел "Популатедирлист Flags" в [битфлагс, используемый конкретными командами](../extensibility/bitflags-used-by-specific-commands.md) для возможных значений).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|значения|Описание|
|-----------|-----------------|
|SCC_OK|Операция успешно завершена.|
|SCC_E_UNKNOWNERROR|Произошла ошибка.|

## <a name="remarks"></a>Заметки
 Функция обратного вызова передается только этим каталогам и (необязательно) именам файлов, фактически находящиеся в репозитории системы управления версиями.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Коды ошибок](../extensibility/error-codes.md)