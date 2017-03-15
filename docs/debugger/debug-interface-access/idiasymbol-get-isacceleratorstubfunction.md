---
title: "IDiaSymbol::get_isAcceleratorStubFunction | Microsoft Docs"
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
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isAcceleratorStubFunction
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает, соответствует ли символ в символ верхнего уровня функции для шейдера компилированного для сочетаний клавиш, который соответствует вызову `parallel_for_each`.  
  
## Синтаксис  
  
```cpp  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### Параметры  
 `pFlag`  
 \[out\] указатель на `BOOL`, указывающее, соответствует ли символ в символ верхнего уровня функции для шейдера компилированного для сочетаний клавиш, который соответствует вызову `parallel_for_each`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_ОК`; в противном случае передачи `S_FALSE` или код ошибки.  
  
## См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)