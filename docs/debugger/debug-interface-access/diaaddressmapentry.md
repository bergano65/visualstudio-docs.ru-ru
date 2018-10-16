---
title: DiaAddressMapEntry | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a29de8f18a9d3123d73210d0e362c2ae2d32641
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459809"
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