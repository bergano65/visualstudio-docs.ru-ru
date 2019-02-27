---
title: IDiaSectionContrib::get_informational | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_informational method
ms.assetid: 5351e89f-7db1-4f8e-9e57-2dd1c74002e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b00d07b788fe07fbe2e879f01a98929927743a0b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637806"
---
# <a name="idiasectioncontribgetinformational"></a>IDiaSectionContrib::get_informational
Получает флаг, указывающий, содержит ли раздел комментарии или аналогичные сведения.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_informational(
   BOOL* pRetVal
};
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если раздел содержит комментарии или другие сведения; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Примечания
 Обычно в .directive разделе содержатся сведения.

## <a name="see-also"></a>См. также раздел
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)