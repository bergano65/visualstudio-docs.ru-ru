---
title: IDiaStackWalkHelper::symbolForVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01c457947eb84859f2ce92378688dd03c624c86d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638820"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Получает символ, который содержит указанный виртуальный адрес.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT symbolForVA( 
   ULONGLONG     va,
   IDiaSymbol**  ppSymbol
);
```

#### <a name="parameters"></a>Параметры
 `va`

[in] Виртуальный адрес, содержащийся в запрошенный символа. Символ должен быть `SymTagFunctionType` (значение из [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) перечисления).

 `ppSymbol`

[out] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий символ по указанному адресу.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)