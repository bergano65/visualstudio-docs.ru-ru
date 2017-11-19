---
title: "IDiaSession::findInlineFramesByAddr | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 473dfe208f2bc6e7059d278bb681ed02c9a337b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindinlineframesbyaddr"></a>IDiaSession::findInlineFramesByAddr
Возвращает перечисление, которое позволяет клиенту проходить через все фреймы для данного адреса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findInlineFramesByAddr (   
   IDiaSymbol*       parent,   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 [in] `IDiaSymbol` Объект, представляющий родительский объект.  
  
 `isect`  
 [in] Указывает компонент раздел адреса.  
  
 `offset`  
 [in] Указывает компонент смещения адреса.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumSymbols` , содержащий список кадров, которые извлекаются.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)