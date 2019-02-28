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
ms.openlocfilehash: 06ef9eb5969b351d49212e9b940988e7ff14c40e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636181"
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
 Заголовок: Dia2.h

 Библиотека: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)