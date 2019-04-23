---
title: StartTrackingContextWithRoot | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContextWithRoot
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68e80da01a0ab1ad59bbb5bdb06c92c1a11a8ac1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59666238"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Запускает контекст отслеживания с использованием файла ответов, указывающего корневой маркер.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 ([HRESULT]<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) с помощью ([успешно]<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) задан бит, если контекст отслеживания был создан.  
  
## <a name="requirements"></a>Требования  
 **Заголовок.** FileTracker.h  
  
## <a name="see-also"></a>См. также  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
