---
title: "IDiaSymbol::get_isHLSLData | Microsoft Docs"
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
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isHLSLData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает, представляет ли этот символ высокоуровневые сведения о языке шейдера \(HLSL\).  
  
## Синтаксис  
  
```cpp  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `BOOL`, указывающее, представляет ли этот символ данные HLSL.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)