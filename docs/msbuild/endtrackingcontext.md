---
title: EndTrackingContext | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b71f214a745222956c7dc9d582cc7fb2f1cfc427
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579698"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Конц текущего контекста отслеживания.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Возвращаемое значение
**HRESULT** с установленным битом **SUCCEEDED**, если контекст отслеживания был закончен.

## <a name="requirements"></a>Требования
**Заголовок.** *FileTracker.h*

## <a name="see-also"></a>См. также
- [StartTrackingContext](../msbuild/starttrackingcontext.md)
