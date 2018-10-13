---
title: BasicType | Документация Майкрософт
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
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8b99310c3e86ad6e8bfddc66d4fe247a6e91356
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49295819"
---
# <a name="basictype"></a>BasicType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает базовый тип символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## <a name="elements"></a>Элементы  
 btNoType  
 Базовый тип не указан.  
  
 btVoid  
 Базовый тип является `void`.  
  
 btChar  
 Базовый тип является `char` (C/C++ тип).  
  
 btWChar  
 Базовый тип представляет собой расширенный символ (Юникод) (`WCHAR`).  
  
 btInt  
 Базовый тип является `signed int` (C/C++ тип).  
  
 btUInt  
 Базовый тип является `unsigned int` (C/C++ тип).  
  
 btFloat  
 Базовый тип является числом с плавающей запятой (`FLOAT`).  
  
 btBCD  
 Базовый тип — это десятичное число закодированных двоичный файл (`BCD`).  
  
 btBool  
 Базовый тип является логическое значение (`BOOL`).  
  
 btLong  
 Базовый тип является `long int` (C/C++ тип).  
  
 btULong  
 Базовый тип является `unsigned long int` (C/C++ тип).  
  
 btCurrency  
 Базовый тип является валюты.  
  
 btDate  
 Базовый тип является даты и времени (`DATE`).  
  
 btVariant  
 Базовый тип является структурой типа переменной (`VARIANT`).  
  
 btComplex  
 Базовый тип — комплексного числа.  
  
 btBit  
 Базовый тип — несколько.  
  
 btBSTR  
 Базовый тип — строка базовый или binary (`BSTR`).  
  
 btHresult  
 Базовый тип является `HRESULT`.  
  
## <a name="remarks"></a>Примечания  
 Возвращаемые значения в этом перечислении [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)



