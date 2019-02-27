---
title: IDiaSymbol::get_memorySpaceKind | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb6fca61dfaf4577f4818c84e1570739c6d63149
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611455"
---
# <a name="idiasymbolgetmemoryspacekind"></a>IDiaSymbol::get_memorySpaceKind
Извлекает тип пространства памяти.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_memorySpaceKind(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Указатель на `DWORD` , содержащий тип пространства памяти.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)