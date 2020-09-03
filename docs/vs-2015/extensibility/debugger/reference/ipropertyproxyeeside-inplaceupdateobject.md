---
title: 'Ипропертипроксеесиде:: Инплацеупдатеобжект | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c91497815dd18dc138b2eadc462c43785830a033
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199516"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Обновляет данные объекта с помощью заданного объекта данных и возвращает новый объект данных, представляющий новые данные объекта.  
  
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
 окне Объект [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , содержащий новые данные.  
  
 `dataOut`  
 заполняет Возвращает новый `IEEDataStorage` объект, содержащий замененные данные.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод фактически обновляет данные объекта. Данные в возвращенном объекте [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) не обязательно должны совпадать с данными во входящем `IEEDataStorage` объекте, но возвращаемый объект должен отражать текущее значение свойства.  
  
 Объект входящих данных обычно не реализуется в EE. Однако объект, возвращаемый этим методом, всегда реализуется в EE, что позволяет `IEEDataStorage` классу ee реализовать интерфейс в любом нужном классе.  
  
 Метод [функция createreplacementobject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) создает объект данных на основе входящего объекта данных, но не влияет на исходные данные свойства.  
  
## <a name="see-also"></a>См. также:  
 [ипропертипроксеесиде](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
