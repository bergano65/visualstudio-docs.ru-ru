---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA - метод"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Считывает указанное количество байтов, начиная с определенного относительного адреса \(RVA\) виртуальном из исполняемого файла.  
  
## Синтаксис  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Параметры  
 `relativeVirtualAddress`  
 \[in\] RVA в исполняемом файле, с которой начинается чтение.  
  
 `cbData`  
 \[in\] количество байтов, которое необходимо считать.  
  
 `pcbData`  
 \[out\] возвращает число считанных байтов.  
  
 `data[]`  
 \[in, out\] массив, который заполняется с байтами, считанные из файла.  
  
## Заметки  
 Этот метод вызывается кодом поддержки DIA для загрузки байты данных из исполняемого файла с помощью относительный виртуальный адрес.  Этот метод вызывается для поддержки [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  
  
## См. также  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)