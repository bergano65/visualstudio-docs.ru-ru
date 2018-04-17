---
title: IDiaSymbol::get_oemSymbolId | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 582e76f0436b29a7ec571b2170ef810fa5998631
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetoemsymbolid"></a>IDiaSymbol::get_oemSymbolId
Возвращает значение идентификатора символ изготовителя оборудования (OEM).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_oemSymbolId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает OEM внутренне назначен символа идентификатора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор — это уникальное значение, созданный пакет SDK для пометить все символы как уникальный.  
  
 Это свойство применяется только к символам с [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) тип `SymTagCustomType`.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)