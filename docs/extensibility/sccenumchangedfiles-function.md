---
title: Функция SccEnumChangedFiles | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b8fb9c83d8948ca3edc0650e85af6ea8c011abc
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639832"
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
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)