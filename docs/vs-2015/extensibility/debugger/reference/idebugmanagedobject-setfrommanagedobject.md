---
title: 'Идебугманажедобжект:: Сетфромманажедобжект | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fa81c34f18d6f1d3980da8d53c65f5ef58c05f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180591"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает значение экземпляра объекта класса значения из экземпляра класса значений, указанного в качестве параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pManagedObject`  
 окне Интерфейс, представляющий управляемый объект, содержащий новое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод используется для изменения управляемого объекта, представленного объектом [идебугманажедобжект](../../../extensibility/debugger/reference/idebugmanagedobject.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
