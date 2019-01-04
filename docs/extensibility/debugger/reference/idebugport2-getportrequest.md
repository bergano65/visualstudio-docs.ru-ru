---
title: IDebugPort2::GetPortRequest | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7bc68272523100c07879b00b261b86f27023a13b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844620"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Получает описание порта, который ранее использовался для создания порта (если доступно).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppRequest`  
 [out] Возвращает [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) объект, представляющий запрос, который использовался для создания порта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  Возвращает `E_PORT_NO_REQUEST` Если порт не был создан с помощью [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) порт запроса.  
  
## <a name="see-also"></a>См. также  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)