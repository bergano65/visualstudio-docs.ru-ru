---
title: IDebugAddress::GetAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e91b90fd54ea70aed729707e927ad2394d756139
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917683"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Возвращает структуру, описывающий объект и его расположение в пределах ее области или контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 [in, out] Объект [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуру, которая заполняется с помощью данного метода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структуры передается этому методу, который затем заполняет его с помощью соответствующую информацию. Способ интерпретации этой информации зависит от типа возвращаемых сведений и сам обработчик символов. См. в разделе [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) для получения дополнительных сведений.  
  
## <a name="see-also"></a>См. также  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)