---
title: IDiaLineNumber::get_columnNumberEnd | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 567df436093b53432e44e21fb96f0d092b71c81d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617422"
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Получает номер столбца источника от единицы, которой заканчивается выражения или оператора.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает номер столбца, в которой заканчивается выражения или оператора. Если значение равно нулю, сведения о столбце окончания отсутствует.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Значение столбца, возвращаемого этим методом является байтовое смещение в строку в позицию после последнего символа в строке инструкции.

## <a name="see-also"></a>См. также раздел
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)