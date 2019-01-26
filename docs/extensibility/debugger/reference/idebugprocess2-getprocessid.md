---
title: IDebugProcess2::GetProcessId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f3e5632f7b59b355c4cd76f76479d21e232780
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954648"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Получает GUID для этого процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pguidProcessId`  
 [out] Возвращает идентификатор GUID для этого процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Глобальный уникальный идентификатор (GUID) идентифицирует этот процесс от всех других процессов, запущенных в системе.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)