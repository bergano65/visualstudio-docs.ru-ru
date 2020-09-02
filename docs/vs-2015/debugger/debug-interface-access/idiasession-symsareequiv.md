---
title: 'IDiaSession:: Симсарикуив | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150216"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Проверяет, эквивалентны ли два символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `symbolA`  
 окне Первый объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , используемый в сравнении.  
  
 `symbolB`  
 окне Второй `IDiaSymbol` объект, используемый для сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если символы эквивалентны, возвращает `S_OK` ; в противном случае возвращает `S_FALSE` , символы не эквивалентны. В противном случае возвратите код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
