---
title: IDiaSession::symsAreEquiv | Документация Майкрософт
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
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08b091bfca65c2713f822e50a2bcacb5ac3df587
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571534"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSession::symsAreEquiv](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-symsareequiv).  
  
Проверяет, являются ли эквивалентными двух символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



