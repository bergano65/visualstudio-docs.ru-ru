---
title: WriteAllTLogs | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- WriteAllTLogs
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d913c322672999e27a9f03dd609d8e87327a5e51
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568461"
---
# <a name="writealltlogs"></a>WriteAllTLogs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [WriteAllTLogs](https://docs.microsoft.com/visualstudio/msbuild/writealltlogs).  
  
  
Записывает журналы отслеживания для всех потоков и контекстов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] `intermediateDirectory`  
 Каталог, в котором хранится журнал отслеживания.  
  
 [in] `tlogRootName`  
 Имя корневой папки для имени файла журнала.  
  
## <a name="return-value"></a>Возвращаемое значение  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) с [успешно] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) задан бит, если контекст отслеживания был создан.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** FileTracker.h  
  
## <a name="see-also"></a>См. также  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)



