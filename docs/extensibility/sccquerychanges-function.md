---
title: Функция Скккуеричанжес | Документация Майкрософт
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
ms.openlocfilehash: 617f07a11f92ab65f079c7d1b41773494e3d0c8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720852"
---
# <a name="sccquerychanges-function"></a>Функция SccQueryChanges
Эта функция перечисляет заданный список файлов, предоставляя сведения об изменениях имен для каждого файла с помощью функции обратного вызова.

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
 пконтекст

окне Указатель контекста для подключаемого модуля системы управления версиями.

 Nфайлы оставленные

окне Число файлов в массиве `lpFileNames`.

 лпфиленамес

окне Массив имен файлов для получения сведений о.

 пфнкаллбакк

окне Функция обратного вызова для вызова каждого имени файла в списке (Дополнительные сведения см. в [куеричанжесфунк](../extensibility/querychangesfunc.md) ).

 пвкаллердата

окне Значение, которое будет передано в функцию обратного вызова без изменений.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|значения|Описание|
|-----------|-----------------|
|SCC_OK|Процесс запроса успешно завершен.|
|SCC_E_PROJNOTOPEN|Проект не был открыт в системе управления версиями.|
|SCC_E_ACCESSFAILURE|Возникла проблема при доступе к системе управления версиями, возможно, из-за проблем с сетью или состязаниями.|
|SCC_E_NONSPECIFICERROR|Произошла неопределенная или общая ошибка.|

## <a name="remarks"></a>Заметки
 Запрошенные изменения относятся к пространству имен: в частности, переименование, Добавление и удаление файла.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Коды ошибок](../extensibility/error-codes.md)