---
title: THUNK_ORDINAL | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0701706deee68cf2dde522d48f9aa62b9a00142
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481506"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Определяет преобразователь типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Элементы  
 THUNK_ORDINAL_NOTYPE  
 Стандартная преобразователя.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Объект `this` корректором преобразователя.  
  
 THUNK_ORDINAL_VCALL  
 Преобразователь виртуальный вызов.  
  
 THUNK_ORDINAL_PCODE  
 Код P преобразователя.  
  
 THUNK_ORDINAL_LOAD  
 Преобразователь задержки загрузки.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Добавочное trampoline преобразователя (trampoline преобразователь используется скачками вызовы из пространства памяти на другой).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Преобразователь trampoline точки ветви.  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются из вызова [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)