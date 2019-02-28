---
title: IDiaSymbol::get_isCVTCIL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isCVTCIL method
ms.assetid: 711b81fd-9549-44dc-9761-5eb862ed64c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 874e05c0ba738f3730c23dcd092921e4b8c02829
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643868"
---
# <a name="idiasymbolgetiscvtcil"></a>IDiaSymbol::get_isCVTCIL
Получает флаг, указывающий модуль был ли преобразован из модуля общих промежуточного языка (CIL) модуль в машинном коде.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isCVTCIL(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Параметры
 `pFlag`

[out] Возвращает `TRUE` Если модуль был преобразован из CIL в машинный код; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Это свойство доступно из `SymTagCompilandDetails` символ типа (см. в разделе [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md).

## <a name="requirements"></a>Требования

|Требование|Описание|
|-----------------|-----------------|
|Заголовок:|dia2.h|
|Версия:|ПАКЕТ SDK для версии 8.0|

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)