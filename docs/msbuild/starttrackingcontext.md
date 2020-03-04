---
title: StartTrackingContext | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50f62704897d68b0e323b948b8f4ed7e96a10c9a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632112"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

Запускает контекст отслеживания.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>Параметры

[in] `intermediateDirectory`

 Каталог, в котором хранится журнал отслеживания.

[in] `taskName`

 Определяет контекст отслеживания. Это имя используется для создания имени файла журнала.

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED**, если контекст отслеживания был создан.

## <a name="requirements"></a>Требования

 **Заголовок.** *FileTracker.h*
