---
title: IDiaSectionContrib::get_remove | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_remove method
ms.assetid: fd30ab7b-022b-4402-a42a-2d38e274c1b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01b3eef646f9105d651a17b58100aad8b4869c3c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616122"
---
# <a name="idiasectioncontribgetremove"></a>IDiaSectionContrib::get_remove
Получает флаг, указывающий, удален ли раздел, прежде чем оно станет изображением в памяти.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT get_remove ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Параметры
 `pRetVal`

[out] Возвращает `TRUE` Если раздел не для добавления изображения в памяти; в противном случае возвращает `FALSE`.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)