---
title: "IDiaInjectedSource::get_source | Microsoft Docs"
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
  - "IDiaInjectedSource::get_source - метод"
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Возвращает байты исходного кода.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Параметры  
 `cbData`  
 \[in\] число байтов, представляющий размер буфера данных.  
  
 `pcbData`  
 \[out\] возвращает число байтов, представляющий возвращаемых байтов.  If `data` существует  `NULL`после этого  `pcbData` общее число байтов доступных данных.  
  
 `data[]`  
 \[out\] буфер, который нужно заполнять в которых свободно источника.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)