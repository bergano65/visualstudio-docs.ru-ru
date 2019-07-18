---
title: IDiaSymbol::get_isSdl | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6904fc673462a79578549bcf22c2973a5c10c95c
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836439"
---
# <a name="idiasymbolgetissdl"></a>IDiaSymbol::get_isSdl
Указывает, является ли модуль компилируется с параметром/SDL.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_isSdl(
   BOOL *pRetVal);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Указатель на `BOOL` , указывающее, компилируется ли модуль с параметром/SDL.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.

## <a name="see-also"></a>См. также
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)