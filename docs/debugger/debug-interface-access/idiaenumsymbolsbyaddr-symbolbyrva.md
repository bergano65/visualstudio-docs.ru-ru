---
title: IDiaEnumSymbolsByAddr::symbolByRVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByRVA method
ms.assetid: f7828029-f2ee-4ccd-afac-785adc60a4c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38d7b0cb8564743ab35cac20cdcb352cdbca48d3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632593"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyrva"></a>IDiaEnumSymbolsByAddr::symbolByRVA
Помещает перечислитель, выполняя поиск по относительный виртуальный адрес (RVA).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT symbolByRVA ( 
   DWORD**      relativeVirtualAddress,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>Параметры
 relativeVirtualAddress

[in] Адрес относительно начала изображения.

 ppsymbol

[out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий найден символ.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если символ не найден. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)