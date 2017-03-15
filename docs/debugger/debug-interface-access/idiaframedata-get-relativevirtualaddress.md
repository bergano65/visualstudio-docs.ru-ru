---
title: "IDiaFrameData::get_relativeVirtualAddress | Microsoft Docs"
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
  - "IDiaFrameData::get_relativeVirtualAddress - метод"
ms.assetid: de070ef4-6c9d-43ca-911c-5245cbcb8dbe
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaFrameData::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает относительный виртуальный адрес RVA\) \(код для кадра.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает относительный виртуальный адрес кода для кадра.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)