---
title: IDiaSymbol::get_targetRelativeVirtualAddress | Документация Майкрософт
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
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 673146a4af83100e5ea6e92112fd66ec0cc45f15
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569374"
---
# <a name="idiasymbolgettargetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSymbol::get_targetRelativeVirtualAddress](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress).  
  
Возвращает относительный виртуальный адрес (RVA) преобразовать конечный.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_targetRelativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает относительный виртуальный адрес преобразовать конечный.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Данное свойство допустимо только если символ, представленный [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значение `SymTagThunk`.  
  
 «Преобразователь» — это часть кода, который выполняет преобразование между адресное пространство с 32-разрядной памяти (также известный как плоский пространства имен) и 16-разрядное адресное пространство, (известный как сегментированное адресное пространство).  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



