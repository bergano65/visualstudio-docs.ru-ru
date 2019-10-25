---
title: 'Идиаенумсимболс:: Skip | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9252826470decd3cddfabdcc2a00e22037d5de5c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743913"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Пропускает указанное число символов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Параметры
 celt

окне Число пропускаемых символов в последовательности перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE`, если больше нет символов для пропуска.

## <a name="see-also"></a>См. также
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)