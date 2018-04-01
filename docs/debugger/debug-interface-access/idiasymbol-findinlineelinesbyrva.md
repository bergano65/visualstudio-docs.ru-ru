---
title: IDiaSymbol::findInlineeLinesByRVA | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: bc9c5b87933940b2f1f98766c1fd477460bf18b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
Возвращает перечисление, которое позволяет клиенту итерации сведения о номерах строк для всех функций, которые являются встроенными, прямо или косвенно, в этот символ в пределах указанного относительного виртуального адреса (RVA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rva`  
 [in] Указывает адрес как RVA.  
  
 `length`  
 [in] Указывает диапазон адресов, в байтах, покрывающие с этим запросом.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumLineNumbers` , содержащий список номеров строк, возвращаемых.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)