---
title: "IDebugProperty2::GetDerivedMostProperty | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords: IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ac691b8e1c2d28477eb8c07f760eae8909a9633
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Возвращает свойство производного свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetDerivedMostProperty (   
   IDebugProperty2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostProperty (   
   out IDebugProperty2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppDerivedMost`  
 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект, представляющий свойство производного.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_GETDERIVEDMOST_NO_DERIVED_MOST` Если отсутствует свойство производного для извлечения.  
  
## <a name="remarks"></a>Примечания  
 Например, если это свойство описывает объект, реализующий интерфейс `ClassRoot` , но это фактически выделенным `ClassDerived` , производный от `ClassRoot`, этот метод возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объекта описания `ClassDerived` объекта.  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)