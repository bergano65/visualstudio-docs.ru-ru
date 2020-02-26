---
title: StopTrackingAndCleanup | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a80fcde7aeab601791c033bd21effce175b2cb9
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579564"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Останавливает все отслеживание и освобождает память, используемую сеансом отслеживания.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает **HRESULT** с установленным битом **SUCCEEDED**, если отслеживание было остановлено.

## <a name="requirements"></a>Требования
 **Заголовок.** *FileTracker.h*

## <a name="see-also"></a>См. также
- [StartTrackingContext](../msbuild/starttrackingcontext.md)