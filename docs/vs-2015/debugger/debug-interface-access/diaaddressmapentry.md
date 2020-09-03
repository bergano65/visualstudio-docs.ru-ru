---
title: Диааддрессмапентри | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67c0a3e297f3eebfbf44724e64c4989d9bb979fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164359"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Описывает запись в карте адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Элементы  
 `rva`  
 Относительный виртуальный адрес (RVA) в образе A.  
  
 `rvaTo`  
 Относительный виртуальный адрес `rva` сопоставляется в образе б.  
  
## <a name="remarks"></a>Remarks  
 Таблица адресов обеспечивает перевод из одного макета изображения (A) в другой (B). Массив `DiaAddressMapEntry` структур, отсортированных по, `rva` определяет карту адресов.  
  
 Чтобы преобразовать адрес, `addrA` , в образе A в адрес `addrB` в образе B выполните следующие действия.  
  
1. Выполните поиск по карте для записи `e` с максимальным значением, `rva` меньшим или равным `addrA` .  
  
2. Задайте `delta = addrA – e.rva`.  
  
3. Задайте `addrB = e.rvaTo + delta`.  
  
   Массив `DiaAddressMapEntry` структур передается в метод [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
