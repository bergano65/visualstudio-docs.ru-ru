---
title: 'Идебугсинкоператион:: Execute | Документация Майкрософт'
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
ms.openlocfilehash: 25da02e6736cc2f8ac27c82f922bd515e791bef1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576696"
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
 заполняет Параметр объекта, возвращаемый операцией.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_ABORT`|Операция была прервана путем вызова метода `IDebugSyncOperation::InProgressAbort`.|  
  
## <a name="remarks"></a>Заметки  
 Диспетчер отладки процесса в целевом потоке вызывает метод `Execute` синхронно.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)