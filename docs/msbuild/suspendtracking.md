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
ms.openlocfilehash: d48c29b9dcca477c5a5470c443be08d5060b413d
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578116"
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