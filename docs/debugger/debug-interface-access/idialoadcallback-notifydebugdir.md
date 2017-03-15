---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyDebugDir - метод"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Вызывается, когда был найден в каталог отладки exe\-файла.  
  
## Синтаксис  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### Параметры  
 `fExecutable`  
 \[in\] `TRUE` если каталог отладки прочитан из исполняемого файла \(а не файл .dbg\).  
  
 `cbData`  
 \[in\] число байтов данных в каталоге отладки.  
  
 `data[]`  
 \[in\] массив, который заполняется с каталогом отладки.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Код возврата, обычно не учитывается.  
  
## Заметки  
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) этот метод вызывает метод обратного вызова при обнаружении каталог отладки при обработке исполняемый файл.  
  
 Этот метод удаляет необходимости, клиента в метод обратного инженеру исполняемого файла или файла отладки для поддержки отладочные данные за исключением того, найденных в файле pdb.  С этими данными, клиент может распознать тип отладочной информации и находится ли он в исполняемом файле или в файле .dbg.  
  
 Большинство клиентов не требуется, поскольку этот обратный вызов `IDiaDataSource::loadDataForExe` метод прозрачным открывает и pdb\-файлы и файлы .dbg при необходимости, что послужили символы.  
  
## См. также  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)