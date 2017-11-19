---
title: "IDiaSymbol::get_upperBound | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_upperBound method
ms.assetid: a77dcafa-ea3f-45da-826d-8f9b4489a03f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f901c21114728ccf65c90345334b0126fe34413f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetupperbound"></a>IDiaSymbol::get_upperBound
Возвращает символ, представляющий верхнюю границу FORTRAN измерения массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_upperBound (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, который представляет собой верхнюю границу FORTRAN измерения массива.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)