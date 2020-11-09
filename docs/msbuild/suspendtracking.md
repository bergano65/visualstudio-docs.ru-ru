---
title: SuspendTracking | Документы Майкрософт
description: Изучите синтаксис, требования и возвращаемое значение функции SuspendTracking MSBuild, которая приостанавливает отслеживание в текущем контексте.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048086"
---
# <a name="suspendtracking"></a>SuspendTracking

Приостанавливает отслеживание в текущем контексте.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED** , если отслеживание было приостановлено.

## <a name="requirements"></a>Требования

 **Заголовок:** *FileTracker.h*

## <a name="see-also"></a>См. также статью

- [ResumeTracking](../msbuild/resumetracking.md)