---
title: "IDiaLoadCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLoadCallback2 - интерфейс"
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает обратные вызовы из символов DIA поиск процедуры, позволяя ограничения, которое требуется наложить на поиск процессе.  
  
## Синтаксис  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## Методы в том порядке Vtable  
 в дополнение к методам в [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) интерфейс, этот интерфейс предоставляет следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Определяет, если поиск pdb\-файл в оригинале каталог отладки.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../Topic/IDiaLoadCallback2::RestrictReferencePathAccess.md)|Определяет, разрешен найти pdb\-файл в пути, где находится EXE\-файл.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Определяет, если поиск отладочной информации позволяет из файлов .dbg.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Определяет, если поиск файлов pdb разрешен в корневом каталоге системы.|  
  
## Заметки  
 Клиентское приложение реализует этот интерфейс и предоставляет ссылку на него в вызов [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  Не забудьте реализовать все методы [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) интерфейс.  
  
## Требования  
 Заголовок: Dia2.h  
  
 Библиотеки: diaguids.lib  
  
 Библиотеки DLL: msdia80.dll  
  
## См. также  
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)