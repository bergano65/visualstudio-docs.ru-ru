---
title: 'Идиаенумсимболс:: Item | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Item method
ms.assetid: 2bd1ec04-e677-4e32-8e32-33334f1eed77
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42180b8e948b93428dc2db92820be336833dcc56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189679"
---
# <a name="idiaenumsymbolsitem"></a>IDiaEnumSymbols::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает символ с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD        index,  
   IDiaSymbol** symbol  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 index  
 окне Индекс объекта [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) для извлечения. Индекс находится в диапазоне от 0 до `count` -1, где `count` возвращается методом [идиаенумсимболс:: get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md) .  
  
 символ  
 заполняет Возвращает объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий нужный символ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
