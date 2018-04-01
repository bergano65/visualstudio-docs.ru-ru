---
title: IDiaSession::symsAreEquiv | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 550218c2d0c2206cdfe417b0e8faff978f9a21e5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
 Если символы эквивалентны, возвращает `S_OK`; в противном случае возвращает `S_FALSE`, символы не являются эквивалентными. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)