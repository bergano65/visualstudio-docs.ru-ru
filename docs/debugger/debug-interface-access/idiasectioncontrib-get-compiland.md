---
title: IDiaSectionContrib::get_compiland | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_compiland method
ms.assetid: c0496f6f-f8f2-435f-8674-6c32db6c5934
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b920a9f1c3191bfea580df510c7a44c2b7929e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828253"
---
# <a name="idiasectioncontribgetcompiland"></a>IDiaSectionContrib::get_compiland
Извлекает ссылку на символ компилируемого объекта, который участвует в этом разделе.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_compiland ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий единицу компиляции, который участвует в этом разделе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)