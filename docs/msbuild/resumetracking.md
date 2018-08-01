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
ms.openlocfilehash: 2ec83d60046a74484035df9d7a7831d16b48d899
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151185"
---
# <a name="resumetracking"></a>ResumeTracking
Возобновляет отслеживание в текущем контексте.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **HRESULT** с установленным битом **SUCCEEDED**, если отслеживание было возобновлено. Если отслеживание нельзя возобновить, так как контекст был недоступен, возвращается **E_FAIL**.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** *FileTracker.h*  
  
## <a name="see-also"></a>См. также  
 [SuspendTracking](../msbuild/suspendtracking.md)