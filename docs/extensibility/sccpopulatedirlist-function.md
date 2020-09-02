---
title: Функция Сккпопулатедирлист | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ac1c51ac694acadd2efb0cd7d1c5a3f1d66ebc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700554"
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
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 ндирс

окне Число путей к каталогу в `lpDirPaths` массиве.

 лпдирпасс

окне Массив путей к каталогу для проверки.

 пфнпопулате

окне Функция обратного вызова для вызова для каждого пути к каталогу и (при необходимости) имени файла в `lpDirPaths` (см. [попдирлистфунк](../extensibility/popdirlistfunc.md) для получения дополнительных сведений).

 пвкаллердата

окне Значение, которое должно быть передано в функцию обратного вызова без изменений.

 фоптионс

окне Сочетание значений, управляющих обработкой каталогов (см. раздел "Популатедирлист Flags" в [битфлагс, используемый конкретными командами](../extensibility/bitflags-used-by-specific-commands.md) для возможных значений).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Операция успешно завершена.|
|SCC_E_UNKNOWNERROR|Произошла ошибка.|

## <a name="remarks"></a>Remarks
 Функция обратного вызова передается только этим каталогам и (необязательно) именам файлов, фактически находящиеся в репозитории системы управления версиями.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Код ошибки](../extensibility/error-codes.md)
