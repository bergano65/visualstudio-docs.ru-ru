---
title: IDiaEnumSymbolsByAddr::Prev | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81700f73b7a1730a4f74f5340d5928b3662db3b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933495"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Извлекает предыдущий символы в порядке по адресу.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Количество символов в перечислителе требуется получить.  
  
 rgelt  
 [out] Массив, который должен быть заполнен с помощью [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекты, представляющие нужные символы.  
  
 pceltFetched  
 [out] Возвращает количество символов в выбираемых перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если символов нет предыдущего. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод обновляет позицию перечислителя, количество выбранных элементов.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)