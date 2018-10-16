---
title: IDebugDefaultPort2::GetPortNotify | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eca2893f388c4dabb244d042d652d3ab604d88bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103287"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Этот метод возвращает [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) интерфейс для этого порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppPortNotify`  
 [out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило `QueryInterface` метод будет вызван на объект, реализующий [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс для получения [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) интерфейса. Однако существуют обстоятельства, в которых реализуется нужного интерфейса на другой объект. Этот метод скрывает условиях и возвращает `IDebugPortNotify2` интерфейс из самый подходящий объект.  
  
## <a name="see-also"></a>См. также  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)