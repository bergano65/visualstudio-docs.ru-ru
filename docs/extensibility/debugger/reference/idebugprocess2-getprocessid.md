---
title: "IDebugProcess2::GetProcessId | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::GetProcessId
helpviewer_keywords: IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 779420e37f3057651f86273ec7d09368443ad1bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Возвращает идентификатор GUID для этого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pguidProcessId`  
 [out] Возвращает идентификатор GUID для этого процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Глобальный уникальный идентификатор (GUID) определяет, начиная со всех других процессов, запущенных в системе.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)