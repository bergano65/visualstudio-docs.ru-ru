---
title: StopTrackingAndCleanup | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StopTrackingAndCleanup
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4cb07a98728612ae5c0930b23e4f76a5672284aa
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54835112"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Останавливает все отслеживание и освобождает память, используемую сеансом отслеживания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [HRESULT](<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) с установленным битом [SUCCEEDED](<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->), если отслеживание было остановлено.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** FileTracker.h  
  
## <a name="see-also"></a>См. также раздел  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
