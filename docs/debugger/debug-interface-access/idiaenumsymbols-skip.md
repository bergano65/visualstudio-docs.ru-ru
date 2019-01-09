---
title: IDiaEnumSymbols::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 492748dc54f68d4f888b8cfb6ad8e27ec44435d0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918629"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Пропускает заданное число символов в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Количество символов в последовательности перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` при наличии дополнительные символы, не нужно пропустить.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)