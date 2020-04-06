---
title: Функция Scc'ruryInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700481"
---
# <a name="sccqueryinfo-function"></a>Функция SccQueryInfo
Эта функция получает информацию о состоянии для набора выбранных файлов под контролем источника.

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
 pvКонтекст

(в) Структура контекста управления исходным элементом.

 nФайлы

(в) Количество файлов, указанных в массиве, `lpFileNames` и длина массива. `lpStatus`

 lpFileNames

(в) Массив имен файлов, которые необходимо запрашивать.

 lpStatus

(в, вне) Массив, в котором плагин управления исходным источником возвращает флаги статуса для каждого файла. Для получения дополнительной [File Status Code](../extensibility/file-status-code-enumerator.md)информации см.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Запрос был успешным.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, вызванная проблемами сети или раздора. Рекомендуется повторная попытка.|
|SCC_E_PROJNOTOPEN|Проект не находится открытым под контролем исходного кода.|
|SCC_E_NONSPECIFICERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Если `lpFileName` это пустая строка, в настоящее время нет информации о состоянии для обновления. В противном случае это полное имя пути файла, для которого может быть изменена информация о состоянии.

 Массив возврата может быть битовой машкой `SCC_STATUS_xxxx` битов. Для получения дополнительной [File Status Code](../extensibility/file-status-code-enumerator.md)информации см. Система управления исходным источником не может поддерживать все типы битов. Например, `SCC_STATUS_OUTOFDATE` если он не предлагается, бит просто не установлен.

 При использовании этой функции для `MSSCCI` проверки файлов обратите внимание на следующие требования к статусу:

- `SCC_STATUS_OUTBYUSER`устанавливается, когда текущий пользователь проверил файл.

- `SCC_STATUS_CHECKEDOUT`не может `SCC_STATUS_OUTBYUSER` быть установлен, если не установлен.

- `SCC_STATUS_CHECKEDOUT`устанавливается только при проверке файла в назначенном рабочем каталоге.

- Если файл проверяется текущим пользователем в каталог, кроме рабочего `SCC_STATUS_OUTBYUSER` каталога, установлен, но `SCC_STATUS_CHECKEDOUT` не является.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Код состояния файла](../extensibility/file-status-code-enumerator.md)
