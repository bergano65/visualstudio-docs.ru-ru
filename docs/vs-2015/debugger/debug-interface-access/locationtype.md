---
title: LocationType | Документация Майкрософт
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
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d1c9ff2dce8918d5bcc75c8504e5af133ea5e43
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836163"
---
# <a name="locationtype"></a>LocationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает тип данных о географическом положении, содержащихся в символе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Расположение находится в локальном хранилище потока.  
  
 `LocIsRegRel`  
 Расположение относительно регистра.  
  
 `LocIsThisRel`  
 Расположение — `this`— относительный.  
  
 `LocIsEnregistered`  
 Расположение — в регистре.  
  
 `LocIsBitField`  
 Расположением является битовым полем.  
  
 `LocIsSlot`  
 Располагается в слот промежуточного языка MSIL (Microsoft).  
  
 `LocIsIlRel`  
 Расположение — относительно MSIL.  
  
 `LocInMetaData`  
 Расположение находится в метаданных.  
  
 `LocIsConstant`  
 Расположение имеет постоянное значение.  
  
 `LocTypeMax`  
 Количество типов расположение в этом перечислении.  
  
## <a name="remarks"></a>Примечания  
 Свойства, доступные для [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) интерфейс зависят от расположения символа в файле образа. Дополнительные сведения см. в разделе [расположения символов](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)



