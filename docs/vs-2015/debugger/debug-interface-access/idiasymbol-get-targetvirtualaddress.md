---
title: IDiaSymbol::get_targetVirtualAddress | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetVirtualAddress method
ms.assetid: a0a5ce72-95f8-443e-bb4b-8c21194faad0
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 911295730548e905e55a61fa16fc3adc792a1bbb
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64793146"
---
# <a name="idiasymbolgettargetvirtualaddress"></a>IDiaSymbol::get_targetVirtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает виртуальный адрес (VA) преобразовать конечный.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_targetVirtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает VA преобразователь целевого объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Данное свойство допустимо только если символ, представленный [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) значение `SymTagThunk`.  
  
 «Преобразователь» — это часть кода, который выполняет преобразование между адресное пространство с 32-разрядной памяти (также известный как плоский пространства имен) и 16-разрядное адресное пространство, (известный как сегментированное адресное пространство).  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
