---
title: "StartTrackingContext | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StartTrackingContext
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 94ec31194438bd02274bb6a0a222d13f1c66130b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="starttrackingcontext"></a>StartTrackingContext
Запускает контекст отслеживания.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] `intermediateDirectory`  
 Каталог, в котором хранится журнал отслеживания.  
  
 [in] `taskName`  
 Определяет контекст отслеживания. Это имя используется для создания имени файла журнала.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **HRESULT** с установленным битом **SUCCEEDED**, если контекст отслеживания был создан.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** FileTracker.h