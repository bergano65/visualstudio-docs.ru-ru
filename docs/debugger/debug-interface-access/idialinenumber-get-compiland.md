---
title: IDiaLineNumber::get_compiland | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25d990ab019c01daf1f977464211fb72838275a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829054"
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
Извлекает ссылку на символ для единице компиляции, использованное байты изображения текста.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Параметры
 pRetVal

[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект для единице компиляции, использованное байты изображения текста.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)