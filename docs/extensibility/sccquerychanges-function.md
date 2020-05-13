---
title: Функция Scc'ruryChanges (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700495"
---
# <a name="sccquerychanges-function"></a>Функция SccQueryChanges
Эта функция перечисляет данный список файлов, предоставляя информацию об изменениях имени для каждого файла через функцию обратного вызова.

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

(в) Указатель контекста управления исходным элементом.

 nФайлы

(в) Количество файлов `lpFileNames` в массиве.

 lpFileNames

(в) Массив имен файлов для получения информации.

 pfnCallback

(в) Функция обратного вызова для каждого имени файла в списке (подробнее см. [кв. м.](../extensibility/querychangesfunc.md)

 pvCallerData

(в) Значение, которое будет передано без изменений функции обратного вызова.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Процесс запроса завершен успешно.|
|SCC_E_PROJNOTOPEN|Проект не был открыт в управлении исходным источником.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором.|
|SCC_E_NONSPECIFICERROR|Произошла неопределенная или общая ошибка.|

## <a name="remarks"></a>Примечания
 Запрашиваемые изменения относятся к пространству имен: в частности, переименованию, добавлению и удалению файла.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Коды ошибок](../extensibility/error-codes.md)
