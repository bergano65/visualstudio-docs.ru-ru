---
title: 'Идиаинжектедсаурце:: get_source | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b389df8220766ffbdbf865a2b8e70877fe91b3f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743339"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
Извлекает байты исходного кода.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Параметры
 `cbData`

окне Число байтов, представляющее размер буфера данных.

 `pcbData`

заполняет Возвращает число байтов, представляющее возвращаемые байты. Если `data` `NULL`, то `pcbData` — общее количество доступных данных в байтах.

 `data[]`

заполняет Буфер, который должен быть заполнен исходными байтами.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)