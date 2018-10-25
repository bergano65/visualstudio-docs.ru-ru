---
title: IDebugDefaultPort2::GetPortNotify | Документация Майкрософт
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
ms.openlocfilehash: feb21f020f6a470b9fded56939987f0a03333206
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872743"
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило `QueryInterface` метод вызывается для объекта, реализующего [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс для получения [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) интерфейс. Тем не менее существуют обстоятельства, в которых реализуется требуемого интерфейса на другой объект. Этот метод скрывает условиях и возвращает `IDebugPortNotify2` из наиболее подходящего объекта.  
  
## <a name="see-also"></a>См. также  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)