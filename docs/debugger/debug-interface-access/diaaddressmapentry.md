---
title: DiaAddressMapEntry | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 6cadfe96bc0bf0ac0395d93c2ef0b156b9965ed2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964089"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Описывает запись в сопоставлении адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Элементы  
 `rva`  
 Относительный виртуальный адрес (RVA) в образ A.  
  
 `rvaTo`  
 Относительный виртуальный адрес `rva` сопоставляется в образе б.  
  
## <a name="remarks"></a>Примечания  
 Сопоставление адреса предоставляет перевод из одного образа макета (A) в другую (Б). Массив `DiaAddressMapEntry` структур, отсортированных по `rva` определяет сопоставление адресов.  
  
 Для преобразования адреса `addrA`, на рисунке объект с адресом, `addrB`, на рисунке B, выполните следующие действия:  
  
1. Поиск карты для записи, `e`, с наибольшим значением `rva` меньше или равно `addrA`.  
  
2. Задайте `delta = addrA - e.rva`.  
  
3. Задайте `addrB = e.rvaTo + delta`.  
  
   Массив `DiaAddressMapEntry` структуры передается [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
## <a name="see-also"></a>См. также раздел  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)