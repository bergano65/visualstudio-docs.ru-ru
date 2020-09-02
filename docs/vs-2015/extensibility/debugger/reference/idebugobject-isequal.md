---
title: 'Идебугобжект:: Equals | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85252cdaf9fb076ebd4f8000115bcea576531bb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159113"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Сравнивает объект с этим объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pObject`  
 окне Объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий объект для сравнения.  
  
 `pfIsEqual`  
 заполняет Возвращает ненулевое значение ( `TRUE` ), если значения объектов равны; в противном случае возвращает ноль ( `FALSE` ).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Как правило, этот метод может сравнивать адреса значений, представленных `pObject` параметром, и этого объекта [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) . Если адреса равны, объекты можно считать равными.  
  
## <a name="see-also"></a>См. также:  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
