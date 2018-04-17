---
title: IDebugQueryEngine2::GetEngineInterface | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e171805500322ff97feac0155abf50f32296366
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Получает интерфейс отладочных ядра (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppUnk`  
 [out] Возвращает `IUnknown` представляет модуль отладки (DE) и которой можно запрашивать другой допустимый интерфейс связанные с Развернутой (например [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) или [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Полученный интерфейса можно использовать с осторожностью, так как вызов через интерфейсы, полученные из этого метода позволяет обойти диспетчер отладочной сеанса обработки и могут привести к SDM попасть в некорректном состоянии или вызвали ошибку во время отладки.  
  
## <a name="see-also"></a>См. также  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)