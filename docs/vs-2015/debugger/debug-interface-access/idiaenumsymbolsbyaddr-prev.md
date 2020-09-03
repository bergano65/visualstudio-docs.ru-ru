---
title: Идиаенумсимболсбяддр::P версия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7a5debb0ffccffed4077c367d5b008a2a2a7cc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189640"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает предыдущие символы в упорядочении по адресу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Число извлекаемых символов в перечислителе.  
  
 rgelt  
 заполняет Массив, который должен быть заполнен объектами [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющими нужные символы.  
  
 pceltFetched  
 заполняет Возвращает количество символов в полученном перечислителе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если предыдущие символы отсутствуют. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод обновляет расположение перечислителя по количеству извлекаемых элементов.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумсимболсбяддр](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
