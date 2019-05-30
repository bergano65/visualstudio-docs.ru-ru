---
title: Функция SccQueryChanges | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e2b1e504bef3ec9507afcddf4f75bc5f697e843
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353508"
---
# <a name="sccquerychanges-function"></a>Функция SccQueryChanges
Эта функция Перечисляет заданный список файлов, предоставляя сведения об изменениях имени для каждого файла через функцию обратного вызова.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Параметры
 pContext

[in] Подключаемый модуль Контекстный указатель исходного элемента управления.

 nFiles

[in] Число файлов в `lpFileNames` массива.

 lpFileNames

[in] Массив имен файлов требуется получить сведения.

 pfnCallback

[in] Функция обратного вызова для вызова для каждого имени файла в списке (см. в разделе [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) сведения).

 pvCallerData

[in] Без изменений значение, которое будет передано в функцию обратного вызова.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Процесс запроса успешно завершена.|
|SCC_E_PROJNOTOPEN|Проект не был открыт в системе управления версиями.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов.|
|SCC_E_NONSPECIFICERROR|Произошла ошибка не задано или Общие.|

## <a name="remarks"></a>Примечания
 Запрашиваемый для изменяются на пространство имен: в частности, переименование, добавление и удаление файла.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Коды ошибок](../extensibility/error-codes.md)