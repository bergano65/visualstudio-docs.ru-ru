---
title: "IPropertyProxyEESide::InPlaceUpdateObject | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1971b553a355b415543aba8ae8936a69e771976b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Обновляет элемент данных объекта в заданный объект данных и возвращает новый объект данных, предоставляющий данные нового объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Фактически, этот метод обновляет данные объекта. Данные в возвращаемом [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) объекта необязательно должен быть таким же, как данные во входящем `IEEDataStorage` объект, но возвращаемый объект должно отражать текущее значение свойства.  
  
 Объект входящих данных обычно не реализуют EE. Тем не менее, возвращаемый этим методом объект всегда реализуется EE, которая позволяет реализовать EE `IEEDataStorage` интерфейс требуемого любой класс.  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) метод создает объект данных, на основе входящего объекта данных, но не влияет на свойства исходных данных.  
  
## <a name="see-also"></a>См. также  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
