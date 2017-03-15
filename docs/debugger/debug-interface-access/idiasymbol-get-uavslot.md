---
title: "IDiaSymbol::get_uavSlot | Microsoft Docs"
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
ms.assetid: a70648f2-3b25-439f-8099-239ac602515a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_uavSlot
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает область uav.  
  
## Синтаксис  
  
```cpp  
HRESULT get_uavSlot(   
   DWORD* pRetVal);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] указатель на `DWORD`, содержащий ячейку uav.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)