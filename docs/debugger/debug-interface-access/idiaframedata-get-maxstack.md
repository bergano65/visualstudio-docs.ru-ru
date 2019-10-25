---
title: 'IDiaFrameData:: get_maxStack | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_maxStack method
ms.assetid: 2585e13c-c0f3-49fe-9a84-08adb0dbeaa4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc5eaa20c5167897ccb19d5e142656ed314a91e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743528"
---
# <a name="idiaframedataget_maxstack"></a>IDiaFrameData::get_maxStack
Возвращает максимальное число байтов, помещаемых в стек в кадре.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

заполняет Возвращает максимальное число байтов, отправленных в стек.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Заметки
 Значение, возвращаемое этим методом, обычно используется при интерпретации строки программы (см. метод [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) для определения программной строки).

## <a name="see-also"></a>См. также
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)