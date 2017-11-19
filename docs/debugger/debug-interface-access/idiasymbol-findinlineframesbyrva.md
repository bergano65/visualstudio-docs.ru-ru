---
title: "IDiaSymbol::findInlineFramesByRVA | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e7a6d9cb-2726-4ac7-9f38-415ad215bf9c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2d4a66fd29ba79250d82e84f04ec2e256dc2d98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindinlineframesbyrva"></a>IDiaSymbol::findInlineFramesByRVA
Возвращает перечисление, которое позволяет клиенту проходить через все фреймы для указанного относительного виртуального адреса (RVA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findInlineFramesByRVA (    DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rva`  
 [in] Указывает адрес как RVA.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumSymbols` , содержащий список кадров, которые извлекаются.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)