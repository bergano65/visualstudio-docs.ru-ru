---
title: Функция SccEnumchangedFiles (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700907"
---
# <a name="sccenumchangedfiles-function"></a>Функция SccEnumChangedFiles
Учитывая список локальных файлов, эта функция определяет, какие файлы отличаются от соответствующих версий в базе данных управления исходным кодом.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Параметры
 pContext

(в) Указатель контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 cФайлы

(в) Количество имен файлов, `lpFileNames` указанных в массиве. Также указывается размер `plIsFileDifferent` массива.

 lpFileNames

(в) Массив локальных имен файлов для проверки.

 plIsFileDifferent

(в, вне) Массив значений, указывающих на статус разницы каждого `cFiles` файла (массив должен иметь по крайней мере записи). Nonzero означает, что файл отличается.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Operation completed successfully (Операция выполнена успешно).|
|SCC_UNSPECIFIEDERROR|Общая ошибка.|

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
