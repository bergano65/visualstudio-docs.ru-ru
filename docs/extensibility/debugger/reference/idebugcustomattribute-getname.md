---
title: IDebugCustomAttribute::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 753964c19c27709af1adf7b38e92555a46559776
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944701"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Получает имя настраиваемого атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrName`  
 [out] Возвращает строку, содержащую имя настраиваемого атрибута.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Именованный возвращаемого этим методом соответствует имени класса, используемого для объявления атрибута. Это может не совсем соответствовать имя самого класса настраиваемого атрибута как C# позволяет суффикс «Attribute» будет удален из имени настраиваемого атрибута, при использовании в объявлении.  
  
## <a name="see-also"></a>См. также  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)