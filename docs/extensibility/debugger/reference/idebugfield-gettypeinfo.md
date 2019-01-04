---
title: IDebugField::GetTypeInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea9f8463bf140b8e3481566948cb5c8e586e9db0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988641"
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Сведения зависят от типов бы включать, например, домен приложения, модуль и класс, содержащий символ.  
  
## <a name="see-also"></a>См. также  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)