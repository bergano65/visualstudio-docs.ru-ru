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
ms.openlocfilehash: ee30bf031761fa7920dadad04d8f17a1bcc0b3a2
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631995"
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