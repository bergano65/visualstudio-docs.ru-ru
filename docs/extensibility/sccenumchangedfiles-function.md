---
title: "Функция SccEnumChangedFiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccEnumChangedFiles"
helpviewer_keywords: 
  - "Функция SccEnumChangedFiles"
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Функция SccEnumChangedFiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Получает список локальных файлов, эта функция определяет, какие файлы отличаются от соответствующих версий в базе данных управления исходного кода.  
  
## Синтаксис  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### Параметры  
 pContext  
 \[in\] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 \[in\] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 cFiles  
 \[in\] Количество имен файлов, указанных в `lpFileNames` массива. Также определяет размер `plIsFileDifferent` массива.  
  
 lpFileNames  
 \[in\] Массив имен локального файла для проверки.  
  
 plIsFileDifferent  
 \[in, out\] Массив значений, указывающий состояние различие каждого файла \(массив должен иметь по крайней мере `cFiles` записи\). Ненулевое значение означает, что файл находится в другой.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Операция успешно завершена.|  
|SCC\_UNSPECIFIEDERROR|Общая ошибка.|  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)