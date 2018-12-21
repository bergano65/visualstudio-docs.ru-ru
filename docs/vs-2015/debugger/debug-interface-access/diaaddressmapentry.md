---
title: DiaAddressMapEntry | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa2824b7fbd10e7628e5c6b0a016615620933df9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756241"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Описывает запись в сопоставлении адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
2. Задайте `delta = addrA – e.rva`.  
  
3. Задайте `addrB = e.rvaTo + delta`.  
  
   Массив `DiaAddressMapEntry` структуры передается [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)



