---
title: IDiaStackFrame::get_allocatesBasePointer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_allocatesBasePointer
ms.assetid: a91e9c8e-c5e3-4887-a60b-f03b5a98f30c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60f39b55ffc14d423d4197765ef89784940f137b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832239"
---
# <a name="idiastackframegetallocatesbasepointer"></a>IDiaStackFrame::get_allocatesBasePointer
Получает флаг, указывающий тип базового указателя, выделяемые для кода в этот диапазон адресов.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если базового указателя выделяется для кода в данном фрейме; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)