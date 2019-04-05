---
title: IDiaSession::symsAreEquiv | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba8c77d7d97da75ce82fcbe732db64acf633b8af
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993270"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
