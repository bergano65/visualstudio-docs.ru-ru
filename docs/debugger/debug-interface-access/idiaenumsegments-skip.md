---
title: IDiaEnumSegments::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff4c5d26d875dc098775d0d379e7d12b062801cd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621530"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Пропускает заданное число сегментов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Параметры
 celt

[in] Количество сегментов в последовательности перечисления для пропуска.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` при наличии не больше сегментов, чтобы пропустить.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)