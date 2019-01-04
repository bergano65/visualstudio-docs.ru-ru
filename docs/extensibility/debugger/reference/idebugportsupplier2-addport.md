---
title: IDebugPortSupplier2::AddPort | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9db20f2034e1c094beb69a3397261c3522589a6c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867856"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Добавляет порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRequest`  
 [in] [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) , описывающий порт, который будет добавляться.  
  
 `ppPort`  
 [out] Возвращает [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) объект, который представляет порт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод фактически создает запрошенный порт, а также добавления поставщика порта внутренний список активных портов. [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) метод может вызываться сначала во избежание возможных простоев много времени.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)