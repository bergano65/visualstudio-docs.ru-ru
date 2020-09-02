---
title: THUNK_ORDINAL | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576412"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Обозначает типы преобразователей.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
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
 Стандартный преобразователь.  
  
 THUNK_ORDINAL_ADJUSTOR  
 `this`Преобразователь регулировки.  
  
 THUNK_ORDINAL_VCALL  
 Преобразователь виртуальных вызовов.  
  
 THUNK_ORDINAL_PCODE  
 Преобразователь P-code.  
  
 THUNK_ORDINAL_LOAD  
 Преобразователь задержек загрузки.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Добавочный преобразователь трамполине (преобразователь трамполине используется для возврата вызовов из одного пространства памяти в другое).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Преобразователь трамполине точки ветвления.  
  
## <a name="remarks"></a>Remarks  
 Значения в этом перечислении возвращаются из вызова метода [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
