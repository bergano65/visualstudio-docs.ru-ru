---
title: Идебугпоинтеробжект::D ереференце | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 40a0e66e5f3cb3a50618a3c8dd4fd5926c34c624
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201006"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает объект, на который указывает.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Простое смещение в байтах от начала объекта, на который указывает.  
  
 `ppObject`  
 заполняет Возвращает объект [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , представляющий объект, на который указывает, а также смещение, если оно есть.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки. Возвращает E_FAIL, если этот объект не указывает на другой объект.  
  
## <a name="remarks"></a>Remarks  
 Объект, на который указывает, может быть примитивом или более сложным типом, например классом или структурой.  
  
## <a name="see-also"></a>См. также:  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
