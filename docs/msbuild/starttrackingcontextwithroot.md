---
title: StartTrackingContextWithRoot | Документы Майкрософт
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53f2c1ebd5896eaa8a4b9d5ff4e5cb7856a1f8e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690494"
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
 **HRESULT** с установленным битом **SUCCEEDED**, если контекст отслеживания был создан.

## <a name="requirements"></a>Требования
 **Заголовок.** *FileTracker.h*

## <a name="see-also"></a>См. также
- [StartTrackingContext](../msbuild/starttrackingcontext.md)