---
title: IDiaEnumSectionContribs::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c90c2148fc5a563fef8946bd39acf4603d7d09f6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601144"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Пропускает заданное число разделе вклад в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Параметры
 `celt`

[in] Номер раздела вклад в последовательности перечисления для пропуска.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` при публикации не дополнительные раздел, чтобы пропустить.

## <a name="see-also"></a>См. также раздел
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)