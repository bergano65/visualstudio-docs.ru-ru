---
title: ResumeTracking | Документы Майкрософт
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632502"
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

 **Заголовок.** *FileTracker.h*

## <a name="see-also"></a>См. также

- [SuspendTracking](../msbuild/suspendtracking.md)