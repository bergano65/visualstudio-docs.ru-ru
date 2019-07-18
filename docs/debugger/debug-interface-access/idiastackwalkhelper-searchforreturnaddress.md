---
title: IDiaStackWalkHelper::searchForReturnAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::searchForReturnAddress method
ms.assetid: 904223b1-6e26-4980-b310-d0b222cdbbbd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87518257d9cab91976f69dd03c9026b0800a0680
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837905"
---
# <a name="idiastackwalkhelpersearchforreturnaddress"></a>IDiaStackWalkHelper::searchForReturnAddress
Выполняет поиск указанного кадра стека для ближайшего обратный адрес функции.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT searchForReturnAddress( 
   IDiaFrameData*  frame,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Параметры
 `frame`

[in] [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий текущий кадр стека.

 `returnAddress`

[out] Возвращает обратный адрес ближайшего функции.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)