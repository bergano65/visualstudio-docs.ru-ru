---
title: IDiaSymbol::get_thunkOrdinal | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8af5be5e094d01d5015fdd181be6d7348d6ff68
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568992"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSymbol::get_thunkOrdinal](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-thunkordinal).  
  
Извлекает тип преобразователя значения функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает значение из [перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) перечисление, указывающее тип преобразователя значения функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Данное свойство допустимо только если символ, представленный [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значение `SymTagThunk`.  
  
 «Преобразователь» — это часть кода, который выполняет преобразование между адресное пространство с 32-разрядной памяти (также известный как плоский пространства имен) и 16-разрядное адресное пространство, (известный как сегментированное адресное пространство).  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



