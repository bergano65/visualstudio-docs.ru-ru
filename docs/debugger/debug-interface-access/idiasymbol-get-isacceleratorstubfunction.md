---
title: IDiaSymbol::get_isAcceleratorStubFunction | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2314142f2080b25a81610ee74f3f627d151651f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956580"
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