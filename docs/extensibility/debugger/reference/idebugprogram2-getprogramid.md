---
title: IDebugProgram2::GetProgramId | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67a132250d036be11c4b7db2f2352b1d6d86793b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938033"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Возвращает идентификатор GUID для этой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProgramId(   
   GUID* pguidProgramId  
);  
```  
  
```csharp  
int GetProgramId(   
   out Guid pguidProgramId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pguidProgramId`  
 [out] Возвращает `GUID` для этой программы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Отладчик (DE) должен возвращать идентификатор программы, которая изначально была передана [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) или [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) методы. Благодаря этому код программы в отладчике компонентов.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)