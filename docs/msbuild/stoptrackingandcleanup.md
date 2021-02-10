---
title: StopTrackingAndCleanup | Документы Майкрософт
description: Узнайте об использовании StopTrackingAndCleanup в MSBuild для остановки отслеживания и освобождения памяти, используемой сеансом отслеживания.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905234"
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

 **Заголовок:** *FileTracker.h*

## <a name="see-also"></a>См. также статью

- [StartTrackingContext](../msbuild/starttrackingcontext.md)