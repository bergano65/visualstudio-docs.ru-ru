---
title: IDiaFrameData::get_type | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_type method
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90a7096550dc3de67ba38058c4029a6bd3c30ca4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830240"
---
# <a name="idiaframedatagettype"></a>IDiaFrameData::get_type
Извлекает тип пакета специфичные для компилятора.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает значение из [перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md) перечисление, указывающее тип кадра специфичные для компилятора.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)