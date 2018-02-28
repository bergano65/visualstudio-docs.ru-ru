---
title: "IDiaSymbol::findChildrenEx | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2eb4bc5492797280845120bd34ae4bbc89f4dd95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Получает дочерние элементы символа. Локальные символы, которые возвращаются включают сведения о динамической диапазоне, при компиляции программы с оптимизацией на.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findChildrenEx (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
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
  
 `ppResult`  
 [out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) извлечь объект, содержащий список дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если хотя бы один дочерний символ найден, или возвращает `S_FALSE` , если дочерние элементы не были найдены; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод является расширенной версией [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).  
  
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