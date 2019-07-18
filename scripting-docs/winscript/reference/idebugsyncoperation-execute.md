---
title: IDebugSyncOperation::Execute | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2bc204169ff94a240e363eb8caa35ec8c7de9be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004874"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Синхронно выполняет операцию и возвращает.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
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
 Диспетчер отладки процессов в целевой поток вызывает `Execute` метод синхронно.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)