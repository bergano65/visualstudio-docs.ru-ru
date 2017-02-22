---
title: "POPDIRLISTFUNC | Microsoft Docs"
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
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "Функция обратного вызова POPDIRLISTFUNC"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Это функция обратного вызова, присвоенное [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) функция для обновления коллекции каталогов и \(необязательно\) имена файлов, чтобы узнать, что в системе управления версиями.  
  
 `POPDIRLISTFUNC` Обратного вызова должен быть вызван только для этих имен файлов и папок \(в списке, присвоенное `SccPopulateDirList` функции\), которые на самом деле в системе управления версиями.  
  
## Подпись  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## Параметры  
 pvCallerData  
 \[in\] Присвоенное значение пользователя [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 \[in\] `TRUE` Если имя в `lpDirectoryOrFileName` является каталогом; в противном случае имя является именем файла.  
  
 lpDirectoryOrFileName  
 \[in\] Полный путь к локальному каталогу или файлу имя, в системе управления версиями.  
  
## Возвращаемое значение  
 IDE возвращает соответствующего кода ошибки:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Продолжайте обработку.|  
|SCC\_I\_OPERATIONCANCELED|Остановите обработку.|  
|SCC\_E\_xxx|Любой соответствующий источник ошибки управления следует остановить обработку.|  
  
## Заметки  
 Если `fOptions` параметр `SccPopulateDirList` функция содержит `SCC_PDL_INCLUDEFILES` флаг, то список будет содержать имена файлов, а также имена каталогов.  
  
## См. также  
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Коды ошибок](../extensibility/error-codes.md)