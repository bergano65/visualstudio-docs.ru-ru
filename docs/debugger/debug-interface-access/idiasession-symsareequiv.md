---
title: IDiaSession::symsAreEquiv | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91a3081cc32eb4286ed7b981dfa2a070dbf4a0ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036697"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Проверяет, являются ли эквивалентными двух символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `symbolA`  
 [in] Первый [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, используемый для сравнения.  
  
 `symbolB`  
 [in] Второй `IDiaSymbol` объект, используемый для сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение, если символы эквивалентны, `S_OK`; в противном случае возвращает `S_FALSE`, символы не эквивалентны. В противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)