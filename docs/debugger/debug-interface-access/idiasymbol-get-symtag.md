---
title: IDiaSymbol::get_symTag | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symTag method
ms.assetid: 139a35bd-faeb-4878-be72-394dedfbb18f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 258203c8f78a009e398468857cd090c916c15885
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606749"
---
# <a name="idiasymbolgetsymtag"></a>IDiaSymbol::get_symTag
Получает классификатор тип символа.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_symTag ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает значение из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисление, указывающее тип классификатора символ.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="example"></a>Пример

```C++
IDiaSymbol* pType;
DWORD       tag = 0;
pType->get_symTag( &tag );
```

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)