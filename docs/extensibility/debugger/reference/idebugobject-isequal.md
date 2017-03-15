---
title: "IDebugObject::IsEqual | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 9
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35d65729a75d06cb8aefc330441cefb09c95bb04
ms.lasthandoff: 02/22/2017

---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Сравнивает объект с данным объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```c#  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pObject`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , который представляет объект для сравнения.  
  
 `pfIsEqual`  
 [out] Возвращает ненулевое значение (`TRUE`), если значения объектов равны; в противном случае, возвращает нуль (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Как правило, этот метод можно сравнить адреса значений, представленных `pObject` параметр и это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекта; Если адреса совпадают, объекты можно считаются равными.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
