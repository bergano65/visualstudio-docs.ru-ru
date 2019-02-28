---
title: IDiaSectionContrib::get_share | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_share method
ms.assetid: 05c4c896-4419-4166-8bb2-8d0934dc14b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3a77ec9f1b088b135b3947250841d10eb9aa169
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611364"
---
# <a name="idiasectioncontribgetshare"></a>IDiaSectionContrib::get_share
Получает флаг, указывающий, могут ли разделе совместно в памяти.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_share ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если раздел совместного использования в памяти; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)