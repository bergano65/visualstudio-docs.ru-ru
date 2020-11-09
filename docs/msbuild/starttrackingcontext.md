---
title: StartTrackingContext | Документы Майкрософт
description: Изучите параметры, требования и возвращаемое значение функции StartTrackingContext MSBuild, которая запускает контекст отслеживания.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 13a22e3a20b69f62fe1e7d6c8e97eb80df6de1b6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048155"
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

 **HRESULT** с установленным битом **SUCCEEDED** , если контекст отслеживания был создан.

## <a name="requirements"></a>Требования

 **Заголовок:** *FileTracker.h*
