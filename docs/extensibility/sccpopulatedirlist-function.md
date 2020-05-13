---
title: Функция SccPopulateDirList (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700554"
---
# <a name="sccpopulatedirlist-function"></a>Функция SccPopulateDirList
Эта функция определяет, какие каталоги и (по желанию) файлы хранятся в исходном элементе управления, учитывая список каталогов для изучения.

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

(в) Указатель контекста управления исходным элементом.

 nDirs

(в) Количество путей каталога в `lpDirPaths` массиве.

 lpDirPaths

(в) Массив путей каталога для изучения.

 pfnPopulate

(в) Функция обратного вызова для каждого пути каталога и `lpDirPaths` (по желанию) имя файла в (см. [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) для деталей).

 pvCallerData

(в) Значение, которое должно быть передано без изменений функции обратного вызова.

 fВарианты

(в) Сочетание значений, контролирующих обработку каталогов (см. раздел "PopulateDirList flags" [Bitflags, используемый конкретными командами](../extensibility/bitflags-used-by-specific-commands.md) для возможных значений).

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Успешно завершил операцию.|
|SCC_E_UNKNOWNERROR|Произошла ошибка.|

## <a name="remarks"></a>Примечания
 Только те каталоги и (по желанию) имена файлов, которые фактически находятся в репозитории управления исходным управлением, передаются функции обратного вызова.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Коды ошибок](../extensibility/error-codes.md)
