---
title: "IDiaSymbol::get_numberOfRows | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf3eb110-d07f-4995-b68b-08290aa67d6f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 135e6572f6c46a2109999136289f5e3d02c74a5b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetnumberofrows"></a>IDiaSymbol::get_numberOfRows
Возвращает число строк в матрице.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_numberOfRows(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Указатель на `DWORD` , содержащий количество строк в матрице.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)