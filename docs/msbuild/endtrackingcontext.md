---
title: EndTrackingContext | Документы Майкрософт
description: Сведения о синтаксисе, возвращаемом значении и требованиях для использования задачи EndTrackingContext MSBuild для завершения текущего контекста отслеживания.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90f4c8c4a83a496dba537e74dddfde4ae3f2f21a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877230"
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

**Заголовок:** *FileTracker.h*

## <a name="see-also"></a>См. также статью

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
