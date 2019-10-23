---
title: 'IDiaEnumInjectedSources:: Skip | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Skip method
ms.assetid: 4aad6a51-f2d3-4064-b216-60d830d0a560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2c7ca67581916ad0c68d7eb1b49fd1c15cf9eaf
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744460"
---
# <a name="idiaenuminjectedsourcesskip"></a>IDiaEnumInjectedSources::Skip
Пропускает указанное число внедренных источников в последовательности перечисления.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Параметры
 celt

окне Число пропущенных внедренных источников в последовательности перечисления.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE`, если нет дополнительных внедренных источников для пропуска.

## <a name="see-also"></a>См. также
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)