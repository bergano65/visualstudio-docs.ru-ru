---
title: "LocationType | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3f59f33ef51eee099a8dfe5bbc5c822f217f8cd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="locationtype"></a>LocationType
Указывает тип расположения сведения, содержащиеся в символе.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## <a name="elements"></a>Элементы  
 `LocIsNull`  
 Сведения о расположении недоступны.  
  
 `LocIsStatic`  
 Расположение является статическим.  
  
 `LocIsTLS`  
 Находится в локальном хранилище потока.  
  
 `LocIsRegRel`  
 Расположение относительно регистра.  
  
 `LocIsThisRel`  
 Расположение — `this`— относительный.  
  
 `LocIsEnregistered`  
 Расположение — в регистрах.  
  
 `LocIsBitField`  
 Расположение — в битовом поле.  
  
 `LocIsSlot`  
 Расположение — слот промежуточного языка Майкрософт (MSIL).  
  
 `LocIsIlRel`  
 Расположение — относительно MSIL.  
  
 `LocInMetaData`  
 Расположение — в метаданных.  
  
 `LocIsConstant`  
 Расположение имеет постоянное значение.  
  
 `LocTypeMax`  
 Число типов расположение этого перечисления.  
  
## <a name="remarks"></a>Примечания  
 Свойства, доступные для [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) интерфейс зависят от расположения символов в файле образа. Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)