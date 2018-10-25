---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdbd6ec439fc46b0ecab7621d4f793c1b3e33450
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893485"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод изменяет объект, представляющий визуализатор.  
  
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

