---
title: IDebugManagedObject::GetManagedObject | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9915e4b9096f9e7ac42700012ea55ee23baef46c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823054"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Возвращает интерфейс, который представляет управляемый объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppManagedObject`  
 [out] Возвращает интерфейс, который представляет управляемый объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Можно запросить любой интерфейс, реализуемый управляемого класса, что позволяет вызывать его методы интерфейса, возвращаемый этим методом.  
  
## <a name="see-also"></a>См. также  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)