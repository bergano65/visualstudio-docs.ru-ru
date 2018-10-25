---
title: IDebugAddress::GetAddress | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 869094fabca44eca352a9610ac59a6627df74dd7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873361"
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