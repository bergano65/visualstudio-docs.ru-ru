---
title: "IDiaStackWalkHelper::symbolForVA | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc9f22d1be5c98e5dd1eda420b1b327aea11741a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Возвращает символ, который содержит указанный виртуальный адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Виртуальный адрес, содержащийся в запрошенной символа. Символ должен быть `SymTagFunctionType` (значение из [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md) перечисления).  
  
 `ppSymbol`  
 [out] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий символ по указанному адресу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)