---
title: Функция Скккуеринфо | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720830"
---
# <a name="sccqueryinfo-function"></a>Функция SccQueryInfo
Эта функция получает сведения о состоянии для набора выбранных файлов в системе управления версиями.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Параметры
 пвконтекст

окне Структура контекста подключаемого модуля системы управления версиями.

 Nфайлы оставленные

окне Число файлов, указанных в массиве `lpFileNames` и длине массива `lpStatus`.

 лпфиленамес

окне Массив имен файлов для запроса.

 лпстатус

[вход, выход] Массив, в котором подключаемый модуль системы управления версиями возвращает флаги состояния для каждого файла. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|значения|Описание|
|-----------|-----------------|
|SCC_OK|Запрос выполнен успешно.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблем с сетью или состязаниями. Рекомендуется повторить попытку.|
|SCC_E_PROJNOTOPEN|Проект не открыт в системе управления версиями.|
|SCC_E_NONSPECIFICERROR|Неконкретный сбой.|

## <a name="remarks"></a>Заметки
 Если `lpFileName` является пустой строкой, в настоящее время нет сведений о состоянии для обновления. В противном случае это полный путь к файлу, сведения о состоянии которого могли измениться.

 Возвращаемый массив может быть битовой маской `SCC_STATUS_xxxx` бит. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md). Система управления версиями может не поддерживать все типы битов. Например, если `SCC_STATUS_OUTOFDATE` не предлагается, бит просто не задан.

 При использовании этой функции для извлечения файлов Обратите внимание на следующие требования к состоянию `MSSCCI`.

- `SCC_STATUS_OUTBYUSER` задается, когда текущий пользователь извлекает файл.

- невозможно задать `SCC_STATUS_CHECKEDOUT`, если не задано значение `SCC_STATUS_OUTBYUSER`.

- `SCC_STATUS_CHECKEDOUT` задается только при извлечении файла в назначенный рабочий каталог.

- Если файл извлечен текущим пользователем в каталог, отличный от рабочего каталога, `SCC_STATUS_OUTBYUSER` задается, но `SCC_STATUS_CHECKEDOUT` не является.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Код состояния файла](../extensibility/file-status-code-enumerator.md)