---
title: IDiaSymbol::get_thunkOrdinal | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed649ffe02cc27f959bf96b826fc02498beb4acd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Возвращает преобразователь типа функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает значение из [thunk_ordinal-перечисление](../../debugger/debug-interface-access/thunk-ordinal.md) перечисления, указывающее тип функции преобразователя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Данное свойство допустимо только тогда, когда символ, представленный [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значение `SymTagThunk`.  
  
 «Преобразователь» — это фрагмент кода, который выполняет преобразование между памяти 32-разрядное адресное пространство (также известный как плоский пространства имен) и 16-разрядном адресном пространстве, (известный как сегментированное адресное пространство).  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)