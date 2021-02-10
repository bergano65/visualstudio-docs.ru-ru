---
title: SetThreadCount | Документы Майкрософт
description: Узнайте, как MSBuild использует SetThreadCount для задания глобального числа потоков и присваивает это число текущему потоку.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966166"
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

 **Заголовок:** *FileTracker.h*