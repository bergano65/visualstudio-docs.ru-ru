---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "DiaAddressMapEntry - перечисление"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Описание записи в сопоставлении адреса.  
  
## Синтаксис  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Elements  
 `rva`  
 Относительный виртуальный адрес \(RVA\) в A. образа.  
  
 `rvaTo`  
 Относительный виртуальный адрес `rva` сопоставляет к б образа.  
  
## Заметки  
 Сопоставление адреса обеспечивает преобразование из одной структуры образа \(a\) другие \(B\).  Массив  `DiaAddressMapEntry` структуры отсортированных by  `rva` определяет сопоставление адреса.  
  
 Перевести адрес `addrA`в образе на адрес, a  `addrB`в б образа, выполните следующие действия:  
  
1.  Найдите сопоставление для записи `e`с самым большим  `rva` меньше или равно  `addrA`.  
  
2.  Установка `delta = addrA – e.rva`.  
  
3.  Установка `addrB = e.rvaTo + delta`.  
  
 Массив  `DiaAddressMapEntry` структуры передаются  [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод.  
  
## Требования  
 Заголовок: dia2.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)