---
title: "IDiaSymbol::get_slot | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_slot method
ms.assetid: 97e405b8-483f-4da0-91e7-ca4d88251ecd
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d188cf52d2250e2a58665b1fe27999a956846159
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetslot"></a>IDiaSymbol::get_slot
Извлекает номер слота расположения. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) — `LocIsSlot`.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_slot (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер слота расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)