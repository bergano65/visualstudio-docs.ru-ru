---
title: Функция SccWillCreateSccFile Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700201"
---
# <a name="sccwillcreatesccfile-function"></a>Функция SccWillCreateSccFile
Эта функция определяет, поддерживает ли плагин управления исходным источником создание MSSCCPRJ. Файл SCC для каждого из данных файлов.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Параметры
 pContext

(в) Указатель контекста управления исходным элементом.

 nФайлы

(в) Количество имен файлов, включенных в `lpFileNames` массив, а `pbSccFiles` также длина массива.

 lpFileNames

(в) Массив полностью квалифицированных имен файлов для проверки (массив должен быть выделен абонентом).

 pbSccFiles

(в, вне) Массив, в котором для хранения результатов.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Успешно.|
|SCC_E_INVALIDFILEPATH|Один из путей в массиве недействителен.|
|SCC_E_NONSPECIFICERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Эта функция вызывается со списком файлов, чтобы определить, обеспечивает ли плагин управления исходным источником поддержку в MSSCCPRJ. Файл SCC для каждого из данных файлов (для получения дополнительной информации о MSSCCPRJ. Файл SCC, [см. SCC файл](../extensibility/mssccprj-scc-file.md)). Плагины управления исходным управлением могут декларировать, есть ли у них возможность создания MSSCCPRJ. SCC файлы, объявив `SCC_CAP_SCCFILE` во время инициализации. Плагин возвращает `TRUE` или `FALSE` на файл `pbSccFiles` в массиве, чтобы указать, какой из данных файлов имеет MSSCCPRJ. Поддержка SCC. Если плагин возвращает код успеха из функции, значения в массиве возврата будут выполнены. При сбое массив игнорируется.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
