---
title: ResumeTracking | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9651197d24e96f58551bca5cfde5ec60b25bfa09
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31577318"
---
# <a name="resumetracking"></a>ResumeTracking
Возобновляет отслеживание в текущем контексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **HRESULT** с установленным битом **SUCCEEDED**, если отслеживание было возобновлено. Если отслеживание нельзя возобновить, так как контекст был недоступен, возвращается **E_FAIL**.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** FileTracker.h  
  
## <a name="see-also"></a>См. также  
 [SuspendTracking](../msbuild/suspendtracking.md)