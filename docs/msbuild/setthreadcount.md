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
ms.openlocfilehash: 5b1eb28d5a54af1708fa8d3ea7a12887174a15bb
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579586"
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