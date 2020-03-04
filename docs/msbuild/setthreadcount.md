---
title: SetThreadCount | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632333"
---
# <a name="setthreadcount"></a>SetThreadCount

Задает глобальный счетчик потоков и назначает его текущему потоку.

## <a name="syntax"></a>Синтаксис

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Параметры

[in] `threadCount`

 Количество потоков для использования.

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED**, если счетчик потоков был обновлен.

## <a name="requirements"></a>Требования

 **Заголовок.** *FileTracker.h*