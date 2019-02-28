---
title: IDiaEnumDebugStreams::Next | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1b7819c90804933795c220c4d47f288d29abfe1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616564"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
Извлекает указанное число потоков отладки в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next ( 
   ULONG                     celt,
   IDiaEnumDebugStreamData** rgelt,
   ULONG*                    pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

[in] Количество потоков отладки в перечислителе требуется получить.

 rgelt

[out] Возвращает массив [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) объектов, представляющих отладочные выполняет потоковую передачу, извлекаемых.

 pceltFetched

[out] Возвращает количество возвращаемых потоков отладки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если отсутствуют дополнительные потоки. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)