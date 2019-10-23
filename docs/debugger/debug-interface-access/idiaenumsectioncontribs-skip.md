---
title: 'Идиаенумсектионконтрибс:: Skip | Документация Майкрософт'
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
ms.openlocfilehash: cb371d841c10b64895400f66bf73159f27d68ec1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744253"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Пропускает указанное число вкладов разделов в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Параметры
 `celt`

окне Число пропускаемых вкладов раздела в последовательности перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE`, если больше нет вкладов в раздел для пропуска.

## <a name="see-also"></a>См. также
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)