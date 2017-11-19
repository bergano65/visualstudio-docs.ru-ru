---
title: "IDebugApplication::StartDebugSession | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.StartDebugSession
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aea5caead4921206428c2f1f36b74d057c8cef36
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
Начинается по умолчанию отладчик интегрированную среду разработки (IDE) и присоединяет сеанс отладки для этого приложения, если один еще не подключен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется для выполнения отладки на времени.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)