---
title: Функция SccQueryInfo | Документация Майкрософт
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
ms.openlocfilehash: 25a4b9b7d07b74047890c4ba56583cc09a394368
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353528"
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
 pvContext

[in] Структура подключаемого модуля контекста исходного элемента управления.

 nFiles

[in] Число файлов, указанных в `lpFileNames` массива и длину `lpStatus` массива.

 lpFileNames

[in] Массив имен файлов к запросам.

 lpStatus

[in, out] Массив, в котором подключаемый модуль системы управления версиями Возвращает флаги состояния для каждого файла. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Запрос выполнен успешно.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, причиной проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|
|SCC_E_PROJNOTOPEN|Проект не открыт в системе управления версиями.|
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка.|

## <a name="remarks"></a>Примечания
 Если `lpFileName` является пустой строкой, в настоящее время отсутствуют сведения о состоянии для обновления. В противном случае — это полный путь имя файла, для которого были изменены сведения о состоянии.

 Массиву возвращаемых значений могут быть битовой `SCC_STATUS_xxxx` bits. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md). Система управления версиями может не поддерживать все типы бит. Например если `SCC_STATUS_OUTOFDATE` не предоставляется, просто не бита.

 При использовании этой функции для извлечения файлов, обратите внимание на следующие `MSSCCI` состояние требований:

- `SCC_STATUS_OUTBYUSER` задается, если текущий пользователь извлек файл.

- `SCC_STATUS_CHECKEDOUT` нельзя назначить Если `SCC_STATUS_OUTBYUSER` имеет значение.

- `SCC_STATUS_CHECKEDOUT` задается только если файл извлечен в указанный рабочий каталог.

- Если файл извлечен текущим пользователем в каталоге, отличном от рабочем каталоге, `SCC_STATUS_OUTBYUSER` устанавливается, но `SCC_STATUS_CHECKEDOUT` не является.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Код состояния файла](../extensibility/file-status-code-enumerator.md)