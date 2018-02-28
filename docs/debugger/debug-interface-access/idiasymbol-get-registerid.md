---
title: "IDiaSymbol::get_registerId | Документы Microsoft"
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
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c944869d48c484f7ddf234f4e00a5d10e96f70ae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
Извлекает обозначение регистра расположения при [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) равно `LocIsEnregistered`.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает обозначение регистра расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Если символ относительно регистра, то есть, если символ [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) задано значение `LocIsRegRel`, используйте `get_registerId` метод после вызова, чтобы [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) метод для получения смещения из регистра, где находится символ.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)