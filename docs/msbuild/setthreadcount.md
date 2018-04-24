---
title: SetThreadCount | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 059c3015bf542dda6a420c80620bc74c9ee6ca6b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="setthreadcount"></a>SetThreadCount
Задает глобальный счетчик потоков и назначает его текущему потоку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] `threadCount`  
 Количество потоков для использования.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **HRESULT** с установленным битом **SUCCEEDED**, если счетчик потоков был обновлен.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** FileTracker.h