---
title: Функция SccPopulateDirList | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateDirList
helpviewer_keywords:
- SccPopulateDirList function
ms.assetid: dfff634b-b155-498b-a356-6eb252ac4fad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74d6008db15cc8cd89daf4882d8952006dc547d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711597"
---
# <a name="sccpopulatedirlist-function"></a>Функция SccPopulateDirList
Эта функция определяет, какие каталоги и (при необходимости) файлы хранятся в системе управления версиями, при наличии списка каталогов для проверки.

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

[in] Подключаемый модуль Контекстный указатель исходного элемента управления.

 nDirs

[in] Количество путей к каталогам в `lpDirPaths` массива.

 lpDirPaths

[in] Массив путей к каталогам для проверки.

 pfnPopulate

[in] Функция обратного вызова для вызова для каждого путь к каталогу и (необязательно) имя файла в `lpDirPaths` (см. в разделе [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) сведения).

 pvCallerData

[in] Без изменений значение, передаваемое функции обратного вызова.

 Возможности

[in] Сочетание значения, определяющие, как обрабатываются каталоги (см. в разделе «Флаги PopulateDirList» [битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md) возможные значения).

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание:|
|-----------|-----------------|
|SCC_OK|Операция успешно выполнена.|
|SCC_E_UNKNOWNERROR|Произошла ошибка.|

## <a name="remarks"></a>Примечания
 Функции обратного вызова, передаются только те каталоги и (необязательно) имена файлов, которые фактически находятся в репозитории системы управления версиями.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)
- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)
- [Коды ошибок](../extensibility/error-codes.md)