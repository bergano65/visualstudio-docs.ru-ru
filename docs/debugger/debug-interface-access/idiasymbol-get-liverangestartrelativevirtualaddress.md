---
title: "IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fe43b99ce430e1e06683494fdeb1c5716b30cea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetliverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Возвращает начало диапазона адресов, в котором локальный символ является допустимой.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_liveRangeStartRelativeVirtualAddress (   
   DWORD* address  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `address`  
 [out] Возвращает дату начала диапазона адресов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращаемый относительный виртуальный адрес — это начало диапазона, в котором символ является допустимой.  
  
> [!NOTE]
>  Возвращен код ошибки означает, что символ имеет сведения о динамической диапазоне.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)