---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "IDiaAddressMap::set_addressMap - метод"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Содержит сопоставление адреса переводы структуры образа поддержки.  
  
## Синтаксис  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### Параметры  
 `cbData`  
 \[in\] количество элементов в `data` параметр.  
  
 `data[]`  
 \[in\] массив [Структура DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) структуры, которые определяют сопоставление перевода.  
  
 `imagetoSymbols`  
 \[in\] `TRUE` если  `data` параметр определяет сопоставление между новой структуры образа, как описано, как восстановить первоначальный \(отладка\) символами.  `FALSE` If  `data` сопоставление с новой структуре образа принятой из исходной структуры.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Обычно DIA извлекает сопоставления перевода адреса из файла базы данных программы \(pdb\).  Если значения отсутствуют, [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) метод вызывается дважды, один раз с  `imagetoSymbols` набор параметров  `TRUE` и раз с  `imagetoSymbols` набор параметров  `FALSE`.  Переводы сопоставления адресов невозможно включить использование [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md) метод если оба сопоставления перевода не предусмотрены.  
  
## См. также  
 [Структура DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)