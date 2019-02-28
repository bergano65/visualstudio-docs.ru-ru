---
title: IDiaStackFrame::get_maxStack | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_maxStack method
ms.assetid: 6352e972-7105-4d0e-aeba-b8fc16d62dec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32e0d8c37b4016412f6dca8772d22baf65799429
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626054"
---
# <a name="idiastackframegetmaxstack"></a>IDiaStackFrame::get_maxStack
Извлекает максимальное число байтов, в стек в кадре.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_maxStack ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает максимальное число байтов, в стек.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)