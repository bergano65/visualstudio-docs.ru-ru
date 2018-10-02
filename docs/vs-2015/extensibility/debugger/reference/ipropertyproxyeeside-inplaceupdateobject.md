---
title: IPropertyProxyEESide::InPlaceUpdateObject | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2d806eec4d5d03b3ac589cca2de5dd6146231723
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572040"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IPropertyProxyEESide::InPlaceUpdateObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject).  
  
Обновляет данные объекта с данным объектом и возвращает новый объект данных, предоставляющий новые данные объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект, содержащий новые данные.  
  
 `dataOut`  
 [out] Возвращает новый `IEEDataStorage` объект, содержащий замененными данными.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Фактически, этот метод обновляет данные объекта. Данные в возвращаемом [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объект не должен быть таким же, как данные во входящем `IEEDataStorage` объект, но возвращаемый объект должен отражать текущее значение свойства.  
  
 Входящий объект данных обычно не реализуют EE. Тем не менее, объект, возвращаемый этим методом всегда реализуется EE, которая позволяет реализовать EE `IEEDataStorage` интерфейс требуется любой класс.  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) метод создает объект данных, на основе входящего объекта данных, но не влияет на свойства исходных данных.  
  
## <a name="see-also"></a>См. также  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)

