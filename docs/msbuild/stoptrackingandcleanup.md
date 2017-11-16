---
title: "StopTrackingAndCleanup | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StopTrackingAndCleanup
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: b38b298c78d549787591aff227d7064287e5480c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Останавливает все отслеживание и освобождает память, используемую сеансом отслеживания.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **HRESULT** с установленным битом **SUCCEEDED**, если отслеживание было остановлено.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** FileTracker.h  
  
## <a name="see-also"></a>См. также  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)