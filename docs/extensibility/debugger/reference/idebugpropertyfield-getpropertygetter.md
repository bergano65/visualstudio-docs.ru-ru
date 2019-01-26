---
title: IDebugPropertyField::GetPropertyGetter | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5df84fc77443cdbc8554b3755385d3cd8682f1b2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041533"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
Возвращает метод, который возвращает свойство.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppField`  
 [out] Возвращает [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) объект, представляющий метод, который возвращает свойство.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы получить метод, который задает свойство, [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) вызовите метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)