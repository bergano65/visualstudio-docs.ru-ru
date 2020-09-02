---
title: 'Иивисуализердатапровидер:: Сетобжектфорвисуализер | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d20164e31f8c42b7099f99ff34ac120319a2def1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540283"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод изменяет объект, который представляет визуализатор.  
  
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
 окне Заданный объект.  
  
 `error`  
 заполняет Если при установке объекта произошла ошибка, то эта строка содержит сообщение об ошибке.  
  
 `pException`  
 заполняет Если произошла ошибка, этот объект содержит сведения об исключении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Разработчик может определить, как возвращаются сведения об ошибке. Однако некоторым вызывающим объектам может показаться, что был возвращен объект исключения, чтобы убедиться в наличии ошибки, поэтому этот метод всегда должен возвращать объект исключения, если произошла ошибка. Строка ошибки также должна указываться в том случае, если вызывающий объект хочет использовать ее.  
  
## <a name="see-also"></a>См. также:  
 [иивисуализердатапровидер](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
