---
title: IDebugObject::IsNullReference | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 027d6364ad3d6277b716d6716d9d02d1390cde6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962945"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Проверяет, является ли этот объект является пустой ссылкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsNullReference(   
   BOOL* pfIsNull  
);  
```  
  
```csharp  
int IsNullReference(  
   out int pfIsNull  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfIsNull`  
 [out] Возвращает ненулевое значение (`TRUE`) Если этот объект является пустой ссылкой; в противном случае возвращает 0 (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Ссылку на null означает, что пустой объект или объект, который не был назначен.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)