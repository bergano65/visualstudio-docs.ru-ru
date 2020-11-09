---
title: StartTrackingContextWithRoot | Документы Майкрософт
description: Узнайте, как использовать StartTrackingContextWithRoot в MSBuild для запуска контекста отслеживания с использованием файла ответов, указывающего корневой маркер.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccca75a0fe525c4e1d9f421b2264070ebda9bdf3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048130"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

Запускает контекст отслеживания с использованием файла ответов, указывающего корневой маркер.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>Параметры

[in] `intermediateDirectory`

 Каталог, в котором хранится журнал отслеживания.

[in] `taskName`

 Определяет контекст отслеживания. Это имя используется для создания имени файла журнала.

[in] `rootMarkerResponseFile`

 Путь к файлу ответов, содержащему корневой маркер. Имя корневой папки, используемое в целях группирования всего отслеживания для контекста.

## <a name="return-value"></a>Возвращаемое значение

 **HRESULT** с установленным битом **SUCCEEDED** , если контекст отслеживания был создан.

## <a name="requirements"></a>Требования

 **Заголовок:** *FileTracker.h*

## <a name="see-also"></a>См. также статью

- [StartTrackingContext](../msbuild/starttrackingcontext.md)