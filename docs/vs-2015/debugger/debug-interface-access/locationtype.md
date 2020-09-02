---
title: Локатионтипе | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28bcaa626797313f6ea68a17da33ef9ea192a856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154202"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает тип сведений о расположении, содержащихся в символе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum LocationType {   
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
 Расположение находится в локальном хранилище потока.  
  
 `LocIsRegRel`  
 Расположение является относительным для регистра.  
  
 `LocIsThisRel`  
 Расположение является `this` относительным.  
  
 `LocIsEnregistered`  
 Расположение находится в регистре.  
  
 `LocIsBitField`  
 Расположение находится в битовом поле.  
  
 `LocIsSlot`  
 Location — это слот MSIL.  
  
 `LocIsIlRel`  
 Расположение относительно MSIL.  
  
 `LocInMetaData`  
 Расположение находится в метаданных.  
  
 `LocIsConstant`  
 Расположение находится в постоянном значении.  
  
 `LocTypeMax`  
 Число типов расположения в этом перечислении.  
  
## <a name="remarks"></a>Remarks  
 Свойства, доступные для интерфейса [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , зависят от расположения символа в файле изображения. Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)
