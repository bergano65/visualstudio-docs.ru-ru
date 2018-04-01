---
title: IDebugEngineLaunch2::CanTerminateProcess | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f4c4157d0c3fcdd3e0de4be4fa2fcf39c16ba67a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Определяет, если процесс может быть завершен.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```csharp  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий завершаемого процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `S_FALSE` Если подсистема не может завершить процесс, например, отказано в доступе.  
  
## <a name="remarks"></a>Примечания  
 Если этот метод возвращает `S_OK`, затем его [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) метод может быть вызван на самом деле завершение процесса.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)