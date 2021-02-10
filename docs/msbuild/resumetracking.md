---
title: ResumeTracking | Документы Майкрософт
description: Изучите синтаксис, требования и возвращаемое значение функции ResumeTracking MSBuild, которая возобновляет отслеживание в текущем контексте.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd6722ca0b930d66a386732dac466a8e4fe36976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937918"
---
# <a name="resumetracking"></a>ResumeTracking

Возобновляет отслеживание в текущем контексте.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED**, если отслеживание было возобновлено. Если отслеживание нельзя возобновить, так как контекст был недоступен, возвращается **E_FAIL**.

## <a name="requirements"></a>Требования

 **Заголовок:** *FileTracker.h*

## <a name="see-also"></a>См. также статью

- [SuspendTracking](../msbuild/suspendtracking.md)