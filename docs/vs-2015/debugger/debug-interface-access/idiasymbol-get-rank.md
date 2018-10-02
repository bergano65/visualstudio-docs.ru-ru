---
title: IDiaSymbol::get_rank | Документация Майкрософт
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
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbf31535c1af5e597ca3fed4d3d878f0277c48f4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562941"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSymbol::get_rank](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-rank).  
  
Возвращает ранг (число измерений) FORTRAN многомерного массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает число измерений в многомерный массив FORTRAN.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Ранг ссылается на число измерений в массиве, где массив объявлен как `myarray[1,2,3]`. В этом примере имеет ранг 3 и 3 измерения. Ранг не относится к C++, который использует концепцию массива массивов для каждого измерения (то есть `myarray[1][2][3]`).  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



