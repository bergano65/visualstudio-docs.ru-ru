---
title: IDebugProcess2::GetServer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetServer
helpviewer_keywords:
- IDebugProcess2::GetServer
ms.assetid: 8f73c530-cceb-4f1f-8c63-1cc0ccd4a310
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ec901ea79c89c18655ddee3f71565fd2437818a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934720"
---
# <a name="idebugprocess2getserver"></a>IDebugProcess2::GetServer
Возвращает сервер, на котором этот процесс выполняется на.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetServer(   
   IDebugCoreServer2** ppServer  
);  
```  
  
```csharp  
int GetServer(   
   out IDebugCoreServer2 ppServer  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppServer`  
 [out] Возвращает [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , представляющий сервер, на котором выполняется этот процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Более одного сервера может выполняться на одном компьютере.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)