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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975c86e0f7674d91b16073c2627414ae1de04081
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841837"
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