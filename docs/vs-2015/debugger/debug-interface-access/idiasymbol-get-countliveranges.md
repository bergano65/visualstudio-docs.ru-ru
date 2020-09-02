---
title: 'IDiaSymbol:: get_countLiveRanges | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_countLiveRanges
ms.assetid: 55f79e1a-d4c2-42cd-ab37-d8253b20e34c
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 066e8d9e6f64984f861a5e14335020c625e96bb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149778"
---
# <a name="idiasymbolget_countliveranges"></a>IDiaSymbol::get_countLiveRanges
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает число допустимых диапазонов адресов, связанных с локальным символом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_countLiveRanges (   
   DWORD* count  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `count`  
 заполняет Возвращает число диапазонов адресов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
