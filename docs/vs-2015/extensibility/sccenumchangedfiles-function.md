---
title: Функция Скценумчанжедфилес | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200132"
---
# <a name="sccenumchangedfiles-function"></a>Функция SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При наличии списка локальных файлов Эта функция определяет, какие файлы отличаются от соответствующих версий в базе данных управления исходным кодом.  
  
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
 окне Указатель контекста для подключаемого модуля системы управления версиями.  
  
 hWnd  
 окне Обработчик окна интегрированной среды разработки, который может использоваться подключаемым модулем системы управления версиями в качестве родительского для любых предоставляемых им диалоговых окон.  
  
 кфилес  
 окне Число имен файлов, указанное в `lpFileNames` массиве. Также указывает размер `plIsFileDifferent` массива.  
  
 лпфиленамес  
 окне Массив имен локальных файлов для проверки.  
  
 плисфиледифферент  
 [вход, выход] Массив значений, указывающий состояние различий для каждого файла (массив должен содержать по крайней мере `cFiles` записи). Ненулевое значение означает, что файл отличается.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Operation completed successfully (Операция выполнена успешно).|  
|SCC_UNSPECIFIEDERROR|Общая ошибка.|  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
