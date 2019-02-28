---
title: IDiaSymbol::get_scoped | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_scoped method
ms.assetid: 588163f7-958e-4072-bf66-db5c5f07d3cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00d7a878edd9b161aa40e4d128196e95ce566a9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639483"
---
# <a name="idiasymbolgetscoped"></a>IDiaSymbol::get_scoped
Получает флаг, указывающий, отображается ли определяемый пользователем тип в неглобальной лексической области.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_scoped ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если определяемый пользователем тип в неглобальной лексической области действия; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)