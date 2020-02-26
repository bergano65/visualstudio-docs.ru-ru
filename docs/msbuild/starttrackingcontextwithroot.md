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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36b48529f82a908ea765151561a71c58cd2c7bc5
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578416"
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