---
title: IDiaSectionContrib::get_code16bit | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4e9c190108cdbf1eb7be2d21927a95fe56fca75
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635895"
---
# <a name="idiasectioncontribgetcode16bit"></a>IDiaSectionContrib::get_code16bit
Получает флаг, указывающий, содержит ли раздел 16-разрядного кода.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_code16bit(
   BOOL *pRetVal
};
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если код в разделе, является 16-разрядным; в противном случае — значение, возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод только указывает, является ли код 16-разрядное. Если код не 16-разрядный, это может быть что-нибудь еще, например, 32-разрядная или 64-разрядный код.

## <a name="see-also"></a>См. также раздел
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)