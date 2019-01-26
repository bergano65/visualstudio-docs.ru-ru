---
title: IDebugCoreServer2::GetPort | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetPort
helpviewer_keywords:
- IDebugCoreServer2::GetPort
ms.assetid: 3f5ea4a8-6085-4600-980a-9e48f8b5be56
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d1bc15f1de05a2474c924f7407353a7a0040d69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021329"
---
# <a name="idebugcoreserver2getport"></a>IDebugCoreServer2::GetPort
Извлекает определенный порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPort(   
   REFGUID       guidPort,  
   IDebugPort2** ppPort  
);  
```  
  
```csharp  
int GetPort(   
   ref Guid        guidPort,  
   out IDebugPort2 ppPort  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidPort`  
 [in] GUID порта для извлечения.  
  
 `ppPort`  
 [out] Возвращает [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) объект, представляющий нужный порт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_PORTSUPPLIER_NO_PORT` Если нет порта с заданным идентификатором.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)