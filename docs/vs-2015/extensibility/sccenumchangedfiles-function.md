---
title: Функция SccEnumChangedFiles | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4254df883bf268f7f473c89d99cdcadf991a8a1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736060"
---
# <a name="sccenumchangedfiles-function"></a>Функция SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
#### <a name="parameters"></a>Параметры  
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
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)

