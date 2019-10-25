---
title: 'Идиаенумсектионконтрибс:: Next | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61d99b0c881abdb8974e94352911ae3234c440c1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744273"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Извлекает указанное число вкладов разделов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Параметры
 celt

окне Количество вкладов разделов в перечислителе, которые необходимо получить.

 rgelt

заполняет Массив, который должен быть заполнен объектами [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) , представляющими нужные вклады разделов.

 pceltFetched

заполняет Возвращает количество вкладов разделов в выбранном перечислителе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE`, если больше нет публикаций разделов. В противном случае возвращается код ошибки.

## <a name="see-also"></a>См. также
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)