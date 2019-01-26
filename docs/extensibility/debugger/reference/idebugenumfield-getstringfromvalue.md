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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b142d8687927ec9951c25b35af1637e52b54486d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945844"
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