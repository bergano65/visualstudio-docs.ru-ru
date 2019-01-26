---
title: IDebugCoreServer2::EnumPortSuppliers | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::EnumPortSuppliers
helpviewer_keywords:
- IDebugCoreServer2::EnumPortSuppliers
ms.assetid: ce0c90e4-8e02-4b08-b558-7677fb2c88f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8610b278b23d4b7be95911af74ccda318d36d9ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942663"
---
# <a name="idebugcoreserver2enumportsuppliers"></a>IDebugCoreServer2::EnumPortSuppliers
Возвращает список всех поставщиков доступный порт.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumPortSuppliers(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int EnumPortSuppliers(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) , содержащий список всех поставщиков порт.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)