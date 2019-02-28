---
title: IDiaSectionContrib::get_relativeVirtualAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relativeVirtualAddress method
ms.assetid: 32f9674d-94f1-4590-99de-a2eb60da4af8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5469bcf8b40dffad0e8a84446d11e3e5eb71e0d0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632190"
---
# <a name="idiasectioncontribgetrelativevirtualaddress"></a>IDiaSectionContrib::get_relativeVirtualAddress
Извлекает изображение относительный виртуальный адрес (RVA) вклад.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает изображение RVA вклада.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)