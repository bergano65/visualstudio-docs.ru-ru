---
title: Функция SccRemove | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70413c2e446f8ed226a58eb8ddfe62ede4a1d61f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338622"
---
# <a name="sccremove-function"></a>Функция SccRemove
Эта функция удаляет файлы из системы управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Параметры
 pvContext

[in] Структура подключаемого модуля контекста исходного элемента управления.

 hWnd

[in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.

 nFiles

[in] Число файлов, указанных в `lpFileNames` массива.

 lpFileNames

[in] Массив имен файлов для удаления полный локальный путь.

 lpComment

[in] Комментарий, который будет применяться для удаления каждого файла.

 Возможности

[in] Команда флаги (неиспользуемого).

 pvOptions

[in] Параметры конкретного подключаемого модуля системы управления версиями.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Удаление выполнено успешно.|
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|
|SCC_E_OPNOTSUPPORTED|Система управления версиями не поддерживает эту операцию.|
|SCC_E_ISCHECKEDOUT|Не удается удалить файл, поскольку он извлечен в данный момент у пользователя.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов.|
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка; файл не был удален.|
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|

## <a name="remarks"></a>Примечания
 Эта функция удаляет файлы из системы управления версиями, но они не удаляются с локального жесткого диска пользователя.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)