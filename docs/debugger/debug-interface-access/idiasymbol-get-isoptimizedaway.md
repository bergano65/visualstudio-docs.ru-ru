---
title: IDiaSymbol::get_isOptimizedAway | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c18b1e38-b152-4a13-aba0-59faded5b2e6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbc5fd2222acff6f667d8b2d83d948619028f7b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993888"
---
# <a name="idiasymbolgetisoptimizedaway"></a>IDiaSymbol::get_isOptimizedAway
Указывает, оптимизирована ли переменная немедленно.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_isOptimizedAway(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Указатель на `BOOL` , указывает ли переменная является отброшено при оптимизации.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)