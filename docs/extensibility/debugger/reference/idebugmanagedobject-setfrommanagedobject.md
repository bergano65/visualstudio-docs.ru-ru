---
title: IDebugManagedObject::SetFromManagedObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a760bb14ea1749e359b5f9deacb6e5918a42423f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54974400"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Задает значение экземпляра класса объекта значения из экземпляра класса значение в качестве параметра указано.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pManagedObject`  
 [in] Интерфейс, который представляет управляемый объект, содержащий новое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод используется для изменения управляемый объект, представленный [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) объекта.  
  
## <a name="see-also"></a>См. также  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)