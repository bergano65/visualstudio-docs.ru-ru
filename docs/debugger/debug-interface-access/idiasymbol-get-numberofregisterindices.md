---
title: "IDiaSymbol::get_numberOfRegisterIndices | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d65c7d052e060cfca7f271fdc89014174055b02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetnumberofregisterindices"></a>IDiaSymbol::get_numberOfRegisterIndices
Возвращает число индексов, регистр.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_numberOfRegisterIndices(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Указатель на `DWORD` , содержащий количество индексов регистра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)