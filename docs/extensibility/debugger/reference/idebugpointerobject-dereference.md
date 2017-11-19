---
title: "IDebugPointerObject::Dereference | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::Dereference
helpviewer_keywords: IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 928a49daf8c4bc2eedbe834a09293fcc767fd2bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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