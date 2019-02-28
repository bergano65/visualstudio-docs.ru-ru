---
title: IDiaSymbol::get_libraryName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_libraryName method
ms.assetid: d04ddd9a-812d-46e4-bd39-28bdf3edfb70
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f832bc0472cc6b04d803dc1e5871eda62bbe451d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605644"
---
# <a name="idiasymbolgetlibraryname"></a>IDiaSymbol::get_libraryName
Возвращает имя файла библиотеки или объекта, из которого был загружен объект.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_libraryName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает имя файла библиотеки или объекта, из которого был загружен объект.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.

## <a name="see-also"></a>См. также раздел
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)