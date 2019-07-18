---
title: IDebugApplicationThread::QueryIsCurrentThread | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d8871d197d662d179fa4d1ed8d420c48ecc5ab3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974570"
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Определяет, является ли этот поток текущим выполняемым потоком.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод выполнен успешно, и это текущим выполняемым потоком.|  
|`S_FALSE`|Это не является текущим выполняемым потоком.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, является ли этот поток текущим выполняемым потоком.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)