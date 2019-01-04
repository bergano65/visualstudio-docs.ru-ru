---
title: IDebugProgram2::GetProcess | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0da808fc2c23fd7d5d5daeb86b6c062a8fe012ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985411"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Получение, на котором выполняется эта программа, в процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppProcess`  
 [out] Возвращает [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, представляющий процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если отладчик (DE) реализует [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) интерфейс, DE реализация этого метода всегда должны возвращать `E_NOTIMPL` поскольку DE не может определить, какой процесс, он выполняется в и, следовательно, не может удовлетворять реализация этого метода.  
  
 Реализация `IDebugEngineLaunch2` интерфейс означает, что DE необходимо знать, как создать процесс; таким образом, DE реализация [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) могут узнать, какой процесс выполняется в интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)