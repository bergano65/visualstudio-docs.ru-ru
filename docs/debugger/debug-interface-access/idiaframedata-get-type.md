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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611494"
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

## <a name="see-also"></a>См. также раздел
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)