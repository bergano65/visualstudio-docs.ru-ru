---
title: IDiaSymbol::get_oemSymbolId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 128b3fa65c3fc48206af2fb66a3a98658a0306ff
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633412"
---
# <a name="idiasymbolgetoemsymbolid"></a>IDiaSymbol::get_oemSymbolId
Возвращает значение идентификатора символа изготовителя оборудования (OEM).

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_oemSymbolId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает OEM внутренне назначенный символ идентификатора.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="remarks"></a>Примечания
 Идентификатор — это уникальное значение, созданные с помощью пакета SDK доступа к интерфейсу отладки, чтобы пометить все символы как уникальный.

 Это свойство применяется только к символам с [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) тип `SymTagCustomType`.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)