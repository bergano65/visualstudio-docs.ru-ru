---
title: 'Идиаенумсимболсбяддр:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc58c8da54380b8a835d64fcc5dc079bb8d8023e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189650"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает следующие символы в упорядочении по адресу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Число извлекаемых символов в перечислителе.  
  
 rgelt  
 заполняет Массив, который должен быть заполнен объектом [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющим нужные символы.  
  
 pceltFetched  
 заполняет Возвращает количество символов в полученном перечислителе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если больше нет символов. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод обновляет расположение перечислителя по количеству извлекаемых элементов.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумсимболсбяддр](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
