---
title: КЕРИРАЗЕВФУНК Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701632"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Это функция обратного вызова, используемая в операции [Scc'eryChanges](../extensibility/sccquerychanges-function.md) для перечисления коллекции имен файлов и определения статуса каждого файла.

 Функция `SccQueryChanges` получает список файлов и указатель `QUERYCHANGESFUNC` на обратный вызов. Плагин управления исходным элементом перечисляет данный список и предоставляет статус (через этот обратный вызов) для каждого файла в списке.

## <a name="signature"></a>Сигнатура

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Параметры
 pvCallerData

(в) Параметр, `pvCallerData` пройденый абонентом (IDE) на [Scc'eryChanges](../extensibility/sccquerychanges-function.md). Плагин управления исходным элементом не должен делать никаких предположений о содержании этого значения.

 pChangesData

(в) Указатель на структуру [структуры КЕЭРИТЕРЕСТЕРСЕСТЕРСЕДА,](#LinkQUERYCHANGESDATA) описывающую изменения в файле.

## <a name="return-value"></a>Возвращаемое значение
 IDE возвращает соответствующий код ошибки:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Продолжайте обработку.|
|SCC_I_OPERATIONCANCELED|Останавливает обработку.|
|SCC_E_xxx|Любая соответствующая ошибка SCC должна прекратить обработку.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>Структура КЕРИТЕНЕСЕСТА
 Структура, передаваемые для каждого файла, выглядит следующим образом:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 dwSize Размер этой структуры (в байтах).

 lpFileName Исходное имя файла для этого элемента.

 dwChangeType Код с указанием статуса файла:

|Код|Описание|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|Не могу сказать, что изменилось.|
|`SCC_CHANGE_UNCHANGED`|Имя не изменяется для этого файла.|
|`SCC_CHANGE_DIFFERENT`|Файл с другим именем, но то же имя существует в базе данных.|
|`SCC_CHANGE_NONEXISTENT`|Файл не существует ни в базе данных, ни локально.|
|`SCC_CHANGE_DATABASE_DELETED`|Файл удален в базе данных.|
|`SCC_CHANGE_LOCAL_DELETED`|Файл удален локально, но файл все еще существует в базе данных. Если это не может `SCC_CHANGE_DATABASE_ADDED`быть определено, вернуться .|
|`SCC_CHANGE_DATABASE_ADDED`|Файл, добавленный в базу данных, но не существует локально.|
|`SCC_CHANGE_LOCAL_ADDED`|Файл не существует в базе данных и является новым локальным файлом.|
|`SCC_CHANGE_RENAMED_TO`|Файл переименован или перемещен в `lpLatestName`базу данных как .|
|`SCC_CHANGE_RENAMED_FROM`|Файл переименован или перемещен в `lpLatestName`базу данных с ; если это слишком дорого отслеживать, верните другой `SCC_CHANGE_DATABASE_ADDED`флаг, например.|

 lpLatestName Текущее имя файла для этого элемента.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Коды ошибок](../extensibility/error-codes.md)
