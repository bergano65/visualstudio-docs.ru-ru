---
title: "StopTrackingAndCleanup | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 43db19d8b7c0d89828b16f4d24c6ffde273130a7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
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