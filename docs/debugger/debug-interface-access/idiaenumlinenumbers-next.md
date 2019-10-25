---
title: 'Идиаенумлиненумберс:: Next | Документация Майкрософт'
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
ms.openlocfilehash: 07402ef7028ecfb7bb5b2c6e33ae06bc98ffe709
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744391"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Извлекает указанное число номеров строк в последовательности перечисления.

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

окне Число возвращаемых номеров строк в перечислителе.

 rgelt

заполняет Возвращает массив объектов [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) , представляющих нужные номера строк.

 pceltFetched

заполняет Возвращает количество номеров строк в выбранном перечислителе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если больше нет номеров строк. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)