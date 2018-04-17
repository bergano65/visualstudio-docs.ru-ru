---
title: IDebugProgram2::GetProcess | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4a0e51725cf809e5c224fd438e507bcfde6ca2c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Получите процесс, в работе программы.  
  
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
 [out] Возвращает [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) интерфейс, который представляет собой процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если отладчик (DE) не реализует [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) интерфейс, DE реализация этого метода всегда должны возвращать `E_NOTIMPL` поскольку DE не может определить процесса, в котором он выполняется в и, следовательно, невозможно удовлетворяет реализацию этого метода.  
  
 Реализация `IDebugEngineLaunch2` интерфейс означает, что DE необходимо знать, как создать процесс; таким образом, DE реализация [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) определить, какой процесс выполняется в интерфейсе.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)