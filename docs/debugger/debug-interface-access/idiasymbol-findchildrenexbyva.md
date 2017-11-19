---
title: "IDiaSymbol::findChildrenExByVA | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::findChildrenExByVA
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94ca67611d77ae7da5f2e3fa1a6e0745871d8e1c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolfindchildrenexbyva"></a>IDiaSymbol::findChildrenExByVA
Получает дочерний символа, действительные в указанный виртуальный адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `symtag`  
 [in] Задает теги символов дочерних элементов, которые требуется получить, как определено в [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md). Значение `SymTagNull` для всех дочерних требуется получить.  
  
 `name`  
 [in] Указывает имя дочерние элементы, которые требуется получить. Значение `NULL` для всех дочерних требуется получить.  
  
 `compareFlags`  
 [in] Задает параметры сравнения для применения к совпадению имен. Значения из [NameSearchOptions-перечисление](../../debugger/debug-interface-access/namesearchoptions.md) перечисления может использоваться отдельно или в сочетании.  
  
 `address`  
 [in] Указывает виртуальный адрес.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) извлечь объект, содержащий список дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если хотя бы один дочерний символ найден, или возвращает `S_FALSE` , если дочерние элементы не были найдены; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Локальные символы, которые возвращаются включают сведения о динамической диапазоне.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)