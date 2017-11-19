---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76a901401e854611cc987ac5c0cf8eeabb8dfd53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Этот метод изменяет объект, представляющий визуализатора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pNewObject`  
 [in] Объект для задания.  
  
 `error`  
 [out] Если возникла ошибка при задании объекта, эта строка содержит сообщение об ошибке.  
  
 `pException`  
 [out] Если произошла ошибка, этот объект содержит сведения об исключении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Он определяется разработчиком для определения того, каким образом возвращаются сведения об ошибке. Однако это возможно, возможно, некоторые вызывающим объектам только внешний вид для просмотра, если объект исключения был возвращен знать, существует ошибка, поэтому этот метод всегда должны возвращать объект исключения, если произошла ошибка. Строка ошибки также должно быть записано в случае, если вызывающий объект хочет, чтобы его использовать.  
  
## <a name="see-also"></a>См. также  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)