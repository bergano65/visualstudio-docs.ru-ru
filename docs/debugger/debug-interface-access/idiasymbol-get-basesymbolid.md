---
title: "IDiaSymbol::get_baseSymbolId | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b0fb7a89e94c8c0e8edb17e6adcfd0c66cae259
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetbasesymbolid"></a>IDiaSymbol::get_baseSymbolId
Извлекает идентификатор символов, из которого указатель мыши на основе.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_baseSymbolId(   
   DWORD *pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Указатель на `DWORD` , содержащий идентификатор символов, из которого указатель мыши на основе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)