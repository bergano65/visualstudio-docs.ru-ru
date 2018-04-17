---
title: IDebugPointerObject::Dereference | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4cc287887baf2530786b03b591d6c03592055e55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Возвращает объект, который указывает.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwIndex`  
 [in] Указывает смещение простой байтов от начала объекта.  
  
 `ppObject`  
 [out] Возвращает [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект представляет объект, на который указывает, а также смещение, если таковые имеются.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки. Возвращает значение E_FAIL, если этот объект не указывает на другой объект.  
  
## <a name="remarks"></a>Примечания  
 Объект, на который указывает может быть примитивом или более сложного типа, например класса или структуры.  
  
## <a name="see-also"></a>См. также  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)