---
title: ПОПДИРЛИСФУНК Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702081"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Это функция обратного вызова, предоставленная функции [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) для обновления коллекции каталогов и (по желанию) имен файлов, чтобы узнать, какие из них находятся под контролем источника.

 Обратный `POPDIRLISTFUNC` вызов должен вызываться только для тех каталогов и `SccPopulateDirList` имен файлов (в списке, отданном функции), которые фактически находятся под контролем источника.

## <a name="signature"></a>Сигнатура

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>Параметры
 pvCallerData

(в) Значение пользователя, присваиваемые [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).

 bFolder

(в) `TRUE` если имя `lpDirectoryOrFileName` в каталоге; в противном случае имя — это имя файла.

 lpDirectoryOrFileName

(в) Полный локальный путь к каталогу или имени файла, накоторомуму ею, находится под контролем исходного кода.

## <a name="return-value"></a>Возвращаемое значение
 IDE возвращает соответствующий код ошибки:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Продолжайте обработку.|
|SCC_I_OPERATIONCANCELED|Останавливает обработку.|
|SCC_E_xxx|Любая соответствующая ошибка управления исходом должна прекратить обработку.|

## <a name="remarks"></a>Примечания
 Если `fOptions` параметр `SccPopulateDirList` функции `SCC_PDL_INCLUDEFILES` содержит флаг, то список, возможно, будет содержать имена файлов, а также имена каталогов.

## <a name="see-also"></a>См. также
- [Функции обратного вызова, реализованные IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [Коды ошибок](../extensibility/error-codes.md)
