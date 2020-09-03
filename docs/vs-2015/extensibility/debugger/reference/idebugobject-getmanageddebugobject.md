---
title: 'Идебугобжект:: Жетманажеддебугобжект | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f2917135f5e25648cf08cd9030e3fdf31aedb52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162476"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает копию управляемого объекта в адресном пространстве модуля отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppObject`  
 заполняет Возвращает объект [идебугманажедобжект](../../../extensibility/debugger/reference/idebugmanagedobject.md) , представляющий созданный управляемый объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки. Возвращает E_FAIL, если этот [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) не представляет экземпляр управляемого класса значения.  
  
## <a name="remarks"></a>Remarks  
 Этот объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) должен представлять экземпляр управляемого класса значения, например `System.Decimal` экземпляр. При наличии локальной копии издержки вызова метода [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) исключаются.  
  
## <a name="see-also"></a>См. также:  
 [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
