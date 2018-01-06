---
title: "IDebugQueryEngine2::GetEngineInterface | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords: IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 65f40bf3e0e110a6d945921d06443f0c8a608d20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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