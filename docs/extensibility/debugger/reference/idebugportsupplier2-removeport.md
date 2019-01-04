---
title: IDebugPortSupplier2::RemovePort | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::RemovePort
helpviewer_keywords:
- IDebugPortSupplier2::RemovePort
ms.assetid: f5c1fbf2-9084-46f2-a682-7db963928df2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf10f7556c548fa4939a6fe8c678513b0575a380
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903855"
---
# <a name="idebugportsupplier2removeport"></a>IDebugPortSupplier2::RemovePort
Удаляет порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT RemovePort(   
   IDebugPort2* pPort  
);  
```  
  
```csharp  
int RemovePort(   
   IDebugPort2 pPort  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pPort`  
 [in] [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий удаляемый порт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод удаляет порт из внутреннего списка активные порты поставщика порта.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)