---
title: IDiaSymbol::get_countLiveRanges | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_countLiveRanges
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbeb17538ccf941303153b211d5bea7b8b9496ad
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetcountliveranges"></a>IDiaSymbol::get_countLiveRanges
Возвращает число допустимый адрес диапазонов, связанных с локальным символом.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_countLiveRanges (   
   DWORD* count  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `count`  
 [out] Возвращает число диапазонов адресов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)