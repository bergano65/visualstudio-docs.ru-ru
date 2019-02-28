---
title: IDiaLineNumber::get_lineNumberEnd | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumberEnd method
ms.assetid: b101853e-2bcf-47c1-acef-e13984c7ea9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb62d8588fdbf439508eed3e5b2cc81a840b9f3d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641641"
---
# <a name="idialinenumbergetlinenumberend"></a>IDiaLineNumber::get_lineNumberEnd
Получает номер строки источника от единицы, которой заканчивается оператор или выражение.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_lineNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает номер строки, в которой заканчивается оператор или выражение. Если значение равно нулю, информация окончания отсутствует.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)