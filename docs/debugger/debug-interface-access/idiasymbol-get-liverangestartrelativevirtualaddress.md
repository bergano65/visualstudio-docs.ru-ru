---
title: IDiaSymbol::get_liveRangeStartRelativeVirtualAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
ms.assetid: 1da52539-9872-4c20-8eaa-74b6cb5f3b02
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b73839b4d9ee0482fc8248b5ebd9f5c61f63552a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639054"
---
# <a name="idiasymbolgetliverangestartrelativevirtualaddress"></a>IDiaSymbol::get_liveRangeStartRelativeVirtualAddress
Возвращает начало диапазона адресов, в котором локальный символ является допустимой.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_liveRangeStartRelativeVirtualAddress ( 
   DWORD* address
);
```

#### <a name="parameters"></a>Параметры
 `address`

[out] Возвращает дату начала диапазона адресов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращается относительный виртуальный адрес — это начало диапазона, в котором символ является допустимой.

> [!NOTE]
>  Возвращен код ошибки означает, что символ не имеет сведения о динамической диапазона.

## <a name="remarks"></a>Примечания

## <a name="requirements"></a>Требования
 Заголовок: Dia2.h

 Библиотека: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)