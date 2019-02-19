---
title: IDiaSymbol::get_liveRangeStartAddressOffset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartAddressOffset
ms.assetid: f5b28914-0a14-4b22-8259-59d7f97ee610
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3a7bf8786f2ca066248ada3f1a0473b85681315
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986999"
---
# <a name="idiasymbolgetliverangestartaddressoffset"></a>IDiaSymbol::get_liveRangeStartAddressOffset
Возвращает компонент смещения начальный адрес диапазона, в котором локальный символ является допустимой.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_liveRangeStartAddressOffset (   
   DWORD* offset  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `offset`  
 [out] Возвращает часть смещения начальный адрес диапазона.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Возвращен код ошибки означает, что символ не имеет сведения о динамической диапазона.  
  
## <a name="remarks"></a>Примечания  
 Адрес, образованное раздела и смещение — это начало диапазона, в котором символ является допустимой.  
  
 Чтобы получить раздел часть адреса, используйте [IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
 Библиотека: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)