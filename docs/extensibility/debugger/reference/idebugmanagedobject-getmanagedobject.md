---
title: IDebugManagedObject::GetManagedObject | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 81b90a43f1de02ba4d195f43b78ee1179c562eff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111200"
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
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Можно запрашивать любой интерфейс, реализуемый управляемого класса, что позволяет вызывать его методы интерфейса, возвращаемый этим методом.  
  
## <a name="see-also"></a>См. также  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)