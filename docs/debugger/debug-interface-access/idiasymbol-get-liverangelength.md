---
title: IDiaSymbol::get_liveRangeLength | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9f1c8caa9e658cfca4e4b2ede8a38b57fcf8713
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624624"
---
# <a name="idiasymbolgetliverangelength"></a>IDiaSymbol::get_liveRangeLength
Возвращает длину диапазона адресов, в котором локальный символ является допустимой.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_liveRangeLength ( 
   ULONGLONG* length
);
```

#### <a name="parameters"></a>Параметры
 `length`

[out] Возвращает длину диапазона адресов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

> [!NOTE]
>  Возвращен код ошибки означает, что символ не имеет сведения о динамической диапазона.

## <a name="remarks"></a>Примечания

## <a name="requirements"></a>Требования
 Заголовок: Dia2.h

 Библиотека: diaguids.lib

 DLL: msdia100.dll

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)