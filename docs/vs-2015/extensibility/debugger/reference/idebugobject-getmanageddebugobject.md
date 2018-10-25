---
title: IDebugObject::GetManagedDebugObject | Документация Майкрософт
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
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07ec736f44529284fbe68e296b1bf6600ef7229e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940571"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Создает копию управляемого объекта в адресном пространстве для обработчика отладки.  
  
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
 [out] Возвращает [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) объект, представляющий только что созданный управляемый объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки. Возвращает значение E_FAIL, если данный [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) не представляет экземпляр класса управляемого значения.  
  
## <a name="remarks"></a>Примечания  
 Это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект должен представлять экземпляр класса управляемого значения, такие как `System.Decimal` экземпляра. Благодаря наличию локальную копию, затраты на вызов [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) исключается.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

