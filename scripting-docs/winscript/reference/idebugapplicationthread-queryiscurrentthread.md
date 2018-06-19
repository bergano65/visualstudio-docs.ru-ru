---
title: IDebugApplicationThread::QueryIsCurrentThread | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 3a291005a7c5b85230c55c736c68de82c0290d0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725624"
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Определяет, является ли этот поток в данный момент поток.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен, и это в данный момент поток.|  
|`S_FALSE`|Не в данный момент поток.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод определяет, является ли этот поток в данный момент поток.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)