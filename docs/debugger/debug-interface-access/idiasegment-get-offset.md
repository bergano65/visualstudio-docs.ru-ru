---
title: IDiaSegment::get_offset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_offset method
ms.assetid: 97415ac6-b072-4e3c-9dd3-73087ae605fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe768bc356f5e3284218d973c31fa41db0bc51ad
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596494"
---
# <a name="idiasegmentgetoffset"></a>IDiaSegment::get_offset
Получает смещение в сегменты, где начинается разделе.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_offset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает смещение, в сегментах, где начинается разделе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)