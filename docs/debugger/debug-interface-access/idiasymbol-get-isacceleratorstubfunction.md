---
title: IDiaSymbol::get_isAcceleratorStubFunction | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2c11cc560be00bd51f8c5ebb35803240c5fbe8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925335"
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Указывает, соответствует ли символ в символ верхнего уровня функции для шейдера, скомпилированные для ускоритель, который соответствует `parallel_for_each` вызова.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pFlag`  
 [out] Указатель на `BOOL` , указывающее, соответствует ли символ в символ функции верхнего уровня для шейдера, скомпилированные для ускоритель, который соответствует `parallel_for_each` вызова.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)