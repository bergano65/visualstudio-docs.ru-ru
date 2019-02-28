---
title: IDiaStackFrame::get_lengthProlog | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthProlog method
ms.assetid: 9894c5ca-835f-41e9-a35e-70e046dfb7f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9ebda7cf7336f9c6a9fc19babf9ed4bbc87fe43
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597184"
---
# <a name="idiastackframegetlengthprolog"></a>IDiaStackFrame::get_lengthProlog
Возвращает число байтов кода пролога в блоке.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_lengthProlog ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает число байтов кода пролога.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)