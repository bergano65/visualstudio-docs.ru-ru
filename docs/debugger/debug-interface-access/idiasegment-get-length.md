---
title: IDiaSegment::get_length | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_length method
ms.assetid: 5d92e394-649b-49f2-bce7-12dd9d666d85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7f559c76bdaf4ca363a374566f4f820cc47dc14
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621777"
---
# <a name="idiasegmentgetlength"></a>IDiaSegment::get_length
Возвращает число байтов в сегменте.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_ length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает число байтов в сегменте.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)