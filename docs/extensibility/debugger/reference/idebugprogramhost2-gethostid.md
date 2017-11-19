---
title: "IDebugProgramHost2::GetHostId | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramHost2::GetHostId
helpviewer_keywords: IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af778ce0f2b5d14a952426abe6d068e7b8ff6b30
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
Получает идентификатор процесса процесса, размещающего эту программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```csharp  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwId`  
 [in, out] [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) структуру, которая заполняется информацией идентификатора процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)