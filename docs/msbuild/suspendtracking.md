---
title: SuspendTracking | Документы Майкрософт
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
ms.openlocfilehash: 950c6a07a46f7f4b970912e576257a577021367e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632020"
---
# <a name="suspendtracking"></a>SuspendTracking

Приостанавливает отслеживание в текущем контексте.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED**, если отслеживание было приостановлено.

## <a name="requirements"></a>Требования

 **Заголовок.** *FileTracker.h*

## <a name="see-also"></a>См. также

- [ResumeTracking](../msbuild/resumetracking.md)