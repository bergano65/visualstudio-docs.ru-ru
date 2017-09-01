---
title: "SetThreadCount | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: d46fea0afc0d6d47a431954dc80a0b58611de0f3
ms.contentlocale: ru-ru
ms.lasthandoff: 06/03/2017

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
