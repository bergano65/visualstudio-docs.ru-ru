---
title: IDebugDefaultPort2::GetServer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f372b815e5c6a68cd5fc1080a5115421de735d27
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038959"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Этот метод получает интерфейс для сервера, на этот порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppServer`  
 [out] Возвращает объект, реализующий интерфейс [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) интерфейс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) реализуется средой Visual Studio и представляет собой сервер, порт, расположенный на.  
  
## <a name="see-also"></a>См. также  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)