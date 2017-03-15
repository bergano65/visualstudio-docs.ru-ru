---
title: "LocationType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LocationType - перечисление"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает тип данных расположения, содержащихся в символе.  
  
## Синтаксис  
  
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
  
## Elements  
 `LocIsNull`  
 Сведения о расположении недоступны.  
  
 `LocIsStatic`  
 Расположение является статическим.  
  
 `LocIsTLS`  
 Расположение в локальном хранилище потока.  
  
 `LocIsRegRel`  
 Расположение регистр\-относительно.  
  
 `LocIsThisRel`  
 Расположение `this`\- relative.  
  
 `LocIsEnregistered`  
 Расположение в регистре.  
  
 `LocIsBitField`  
 В поле расположение.  
  
 `LocIsSlot`  
 Расположение область MSIL.  
  
 `LocIsIlRel`  
 Расположение MSIL\-относительно.  
  
 `LocInMetaData`  
 Расположение в метаданных.  
  
 `LocIsConstant`  
 Расположение в постоянном значения.  
  
 `LocTypeMax`  
 Количество типов расположение внутри этого перечисления.  
  
## Заметки  
 Свойства, доступные для [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) зависит от интерфейса положение символа в файл изображения.  Дополнительные сведения см. в разделе [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Значения в этом перечислении возвращаемых вызовом [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md) метод.  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [Местоположения символов](../../debugger/debug-interface-access/symbol-locations.md)