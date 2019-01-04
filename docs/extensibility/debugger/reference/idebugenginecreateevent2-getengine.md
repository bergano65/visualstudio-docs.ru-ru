---
title: IDebugEngineCreateEvent2::GetEngine | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineCreateEvent2::GetEngine
helpviewer_keywords:
- IDebugEngineCreateEvent2::GetEngine
ms.assetid: 187d24ed-9f9a-4418-a0ef-b8a19f54652c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65ec7a4b1237d98f2693dbb136f712e39041f935
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967817"
---
# <a name="idebugenginecreateevent2getengine"></a>IDebugEngineCreateEvent2::GetEngine
Извлекает объект, представляющий только что созданный отладчик (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetEngine(   
   IDebugEngine2** pEngine  
);  
```  
  
```csharp  
int GetEngine(   
   out IDebugEngine2 pEngine  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pEngine`  
 [out] Возвращает [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , представляющий только что созданный DE.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)