---
title: IDiaSymbol::findInlineFramesByRVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e7a6d9cb-2726-4ac7-9f38-415ad215bf9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4afe0e27955d06ed33e2248298b86a5aaef5f5af
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069308"
---
# <a name="idiasymbolfindinlineframesbyrva"></a>IDiaSymbol::findInlineFramesByRVA
Возвращает перечисление, которое позволяет клиентам выполнять итерацию всех встроенных кадров на указанный относительный виртуальный адрес (RVA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findInlineFramesByRVA (    DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rva`  
 [in] Указывает адрес как RVA.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumSymbols` , содержащий список кадров, которые извлекаются.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)