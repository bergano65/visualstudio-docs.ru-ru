---
title: 'IDiaFrameData:: get_type | Документация Майкрософт'
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
ms.openlocfilehash: a4af060a4a0c36067a07a78166d1cf9cbc62e90e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743482"
---
# <a name="idiaframedataget_type"></a>IDiaFrameData::get_type
Извлекает тип кадра, зависящий от компилятора.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_type ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает значение из перечисления [перечисления стаккфраметипинум](../../debugger/debug-interface-access/stackframetypeenum.md) , которое указывает на тип кадра, зависящий от компилятора.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Перечисление StackFrameTypeEnum](../../debugger/debug-interface-access/stackframetypeenum.md)