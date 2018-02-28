---
title: "IEnumRemoteDebugApplicationThreads::Reset | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IEnumRemoteDebugApplicationThreads.Reset
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumRemoteDebugApplicationThreads::Reset
ms.assetid: a6ad8a01-4cc0-4f9c-9cfe-c7448c753473
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b218b04781f8836b7c2f99d71d20716404777a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ienumremotedebugapplicationthreadsreset"></a>IEnumRemoteDebugApplicationThreads::Reset
Сбрасывает последовательность перечисления в начало.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод сбрасывает последовательность перечисления в начало.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IEnumRemoteDebugApplicationThreads](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)