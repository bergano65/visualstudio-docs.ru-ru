---
title: IDiaSymbol::get_signature | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_signature method
ms.assetid: 0efefa39-49a5-4282-9d41-e50832d927e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43bb848df76304a98a31497a12187235699d417f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638287"
---
# <a name="idiasymbolgetsignature"></a>IDiaSymbol::get_signature
Извлекает значение символа подписи.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_signature ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает значение символа подписи.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)