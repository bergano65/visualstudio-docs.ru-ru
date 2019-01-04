---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8a5b1742372b8fee4227c7d2bca5efa93b42f2c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915511"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Этот метод изменяет объект, представляющий визуализатор.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pNewObject`  
 [in] Задаваемый объект.  
  
 `error`  
 [out] Если произошла ошибка при установке объекта, эта строка содержит сообщение об ошибке.  
  
 `pException`  
 [out] Если произошла ошибка, этот объект содержит сведения об исключении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это зависит от разработчика, чтобы определить, каким образом возвращаются сведения об ошибке. Тем не менее существует возможность, что некоторые вызывающим объектам может только внешний вид, чтобы узнать, был ли объект исключения возвращены знать, существует ошибка, поэтому этот метод всегда должен возвращать объект исключения, если произошла ошибка. Строка ошибки также должен быть предоставлен, в случае, если вызывающий объект хочет, чтобы его использовать.  
  
## <a name="see-also"></a>См. также  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)