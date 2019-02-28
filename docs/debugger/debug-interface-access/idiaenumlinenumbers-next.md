---
title: IDiaEnumLineNumbers::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66abd987e3da4fadaac9d5b2de6664c4ae9e24ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599094"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Возвращает указанное количество номеров строк в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

[in] Число номеров строк в перечислителе требуется получить.

 rgelt

[out] Возвращает массив [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) объекты, представляющие числа нужной строке.

 pceltFetched

[out] Возвращает количество номеров строк в выбранных перечислитель.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` при наличии без несколько номеров строк. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)