---
title: "IDebugSyncOperation::Execute | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69e07c646bfa176f5e2dc07539f301a8ef5c5273
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Синхронно выполняет операцию и возвращает.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppunkResult`  
 [out] Параметр объекта, возвращенное операцией.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_ABORT`|Операция была прервана, вызвав `IDebugSyncOperation::InProgressAbort` метод.|  
  
## <a name="remarks"></a>Примечания  
 Диспетчер отладки процессов в целевом потоке не вызывает `Execute` метод синхронно.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)