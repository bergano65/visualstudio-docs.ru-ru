---
title: IDebugField::GetTypeInfo | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9f1ec3adf1f71d5d7f7e916b261555ca8aeb9d31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Этот метод возвращает сведения зависят от типов символов или типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```csharp  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pTypeInfo`  
 [out] Возвращает сведения о типе в предоставленном [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) структуры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сведения зависят от типов будет включать, например, домен приложения, модуля и класса, который содержит символ.  
  
## <a name="see-also"></a>См. также  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)