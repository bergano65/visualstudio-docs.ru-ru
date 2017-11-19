---
title: "DiaAddressMapEntry | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1324ea79ec60a61e315253573b9d4aa3ced2695
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Описывает запись в сопоставлении адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Элементы  
 `rva`  
 Относительный виртуальный адрес (RVA) в образе A.  
  
 `rvaTo`  
 Относительный виртуальный адрес `rva` сопоставляется в образе б.  
  
## <a name="remarks"></a>Примечания  
 Сопоставление адресов предоставляет перевод из одного образа макета (A) в другую (Б). Массив `DiaAddressMapEntry` структуры, отсортированных по `rva` определяет сопоставление адресов.  
  
 Для перевода адрес `addrA`, рисунке A в адрес `addrB`, в образе B, выполните следующие действия:  
  
1.  Поиск карты для записи, `e`, с наибольшим значением `rva` меньше или равно `addrA`.  
  
2.  Set `delta = addrA - e.rva`.  
  
3.  Set `addrB = e.rvaTo + delta`.  
  
 Массив `DiaAddressMapEntry` структуры передается [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)