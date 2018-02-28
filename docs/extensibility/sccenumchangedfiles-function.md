---
title: "Функция SccEnumChangedFiles | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a3a124bbcadbf798f22b59111637038a09af7d75
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccenumchangedfiles-function"></a>Функция SccEnumChangedFiles
Получив список локальных файлов, эта функция определяет, какие файлы отличаются от соответствующих версий в базе данных системы управления исходного кода.  
  
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
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 cFiles  
 [in] Число имен файлов, указанной в `lpFileNames` массива. Также определяет размер `plIsFileDifferent` массива.  
  
 lpFileNames  
 [in] Массив имен локальный файл для проверки.  
  
 plIsFileDifferent  
 [in, out] Массив значений, указывающее состояние разница каждого файла (массив должен иметь по крайней мере `cFiles` записей). Ненулевое значение означает, что файл отличается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Операция успешно завершена.|  
|SCC_UNSPECIFIEDERROR|Общая ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)