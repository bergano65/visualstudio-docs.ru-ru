---
title: IDebugEnumField::GetStringFromValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb3fc6a0e8aab20659abe7a2d8601f478f948a9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877410"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Этот метод получает имя константы перечисления, учитывая его значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `value`  
 [in] Значение, для которого необходимо получить имя перечисления констант.  
  
 `pbstrValue`  
 [out] Возвращает имя константы перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если значение не имеет связанного имени, либо возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если имеется несколько имен, связанный с тем же значением, возвращается имя определяется в перечислении.  
  
## <a name="see-also"></a>См. также  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)