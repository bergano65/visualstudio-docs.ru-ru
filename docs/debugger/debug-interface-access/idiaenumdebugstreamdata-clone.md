---
title: IDiaEnumDebugStreamData::Clone | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Clone method
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8362fecf12613595b3e96218c704eae26f4e8bbc
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641914"
---
# <a name="idiaenumdebugstreamdataclone"></a>IDiaEnumDebugStreamData::Clone
Создает перечислитель, содержащий же перечисленной последовательности, что и текущий перечислитель.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Clone ( 
   IDiaEnumDebugStreamData** ppenum
);
```

#### <a name="parameters"></a>Параметры
 ppenum

[out] Возвращает [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) объект, который содержит повторяющиеся последовательность записей потока данных отладки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)