---
title: Функция SccEnumChangedFiles | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9bc2738e9a4d7cac0d57b9c613b7070f60baff
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711563"
---
# <a name="sccenumchangedfiles-function"></a>Функция SccEnumChangedFiles
При наличии списка локальных файлов, эта функция определяет, какие файлы отличаются от соответствующие версии в базе данных системы управления исходного кода.

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

[in] Подключаемый модуль Контекстный указатель исходного элемента управления.

 hWnd

[in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.

 cFiles

[in] Количество имен файлов, указанных в `lpFileNames` массива. Также указывает размер `plIsFileDifferent` массива.

 lpFileNames

[in] Массив имен локальный файл для проверки.

 plIsFileDifferent

[in, out] Массив значений, указывающий разницу состояние каждого файла (массив должен иметь по крайней мере `cFiles` записей). Ненулевое значение означает, что файл отличается.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание:|
|-----------|-----------------|
|SCC_OK|Операция успешно завершена.|
|SCC_UNSPECIFIEDERROR|Общая ошибка.|

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)