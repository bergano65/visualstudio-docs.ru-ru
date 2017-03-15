---
title: "IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs"
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
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить, указывающее, соответствует ли символ в локальной переменной общей группой в компилированном коде для сочетаний клавиш C\+\+ AMP.  
  
## Синтаксис  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### Параметры  
 `pFlag`  
 \[out\] указатель на `BOOL`, указывающее, соответствует ли символ в локальной переменной общей группой в компилированном коде для сочетаний клавиш C\+\+ AMP.  Если `TRUE`, `get_baseDataSlot` и методы `get_baseDataOffset` можно использовать для получения сведений о местоположении хранилища для переменной.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get\_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)