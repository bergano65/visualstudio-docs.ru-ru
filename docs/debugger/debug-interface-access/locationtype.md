---
title: LocationType | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e816ac9dca3c70e88ae023b4fda4edf0b99f9c96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872100"
---
# <a name="locationtype"></a>LocationType
Указывает тип данных о географическом положении, содержащихся в символе.  
  
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