---
title: IDiaEnumSymbolsByAddr::Prev | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 689412a832795805d79032e8260503d4ebad8209
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561913"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaEnumSymbolsByAddr::Prev](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev).  
  
Извлекает предыдущий символы в порядке по адресу.  
  
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
 [in] Количество символов в перечислителе требуется получить.  
  
 rgelt  
 [out] Массив, который должен быть заполнен с помощью [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объекты, представляющие нужные символы.  
  
 pceltFetched  
 [out] Возвращает количество символов в выбираемых перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если символов нет предыдущего. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод обновляет позицию перечислителя, количество выбранных элементов.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



