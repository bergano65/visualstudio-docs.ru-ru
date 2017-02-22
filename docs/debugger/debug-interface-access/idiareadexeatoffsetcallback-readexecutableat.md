---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt - метод"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Считывает указанное количество байтов, начиная с конкретного смещения из исполняемого файла.  
  
## Синтаксис  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Параметры  
 fileOffset  
 \[in\] смещение в исполняемом файле, с которой начинается чтение.  
  
 cbData  
 \[in\] количество байтов, которое необходимо считать.  
  
 pcbData  
 \[out\] возвращает число считанных байтов.  
  
 данные \[\]  
 \[in, out\] массив, который заполняется с байтами, считанные из файла.  
  
## Заметки  
 Этот метод вызывается кодом поддержки DIA для загрузки байты данных из исполняемого файла с помощью абсолютное смещение файла.  Этот метод вызывается для поддержки [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  
  
## См. также  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)