---
title: 'Идебуженумфиелд:: Жетстрингфромвалуе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdd60c363e30afbe4c61e8e18660a17a06a5ce8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188998"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод получает имя константы перечисления, учитывая его значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Значение, для которого необходимо получить имя константы перечисления.  
  
 `pbstrValue`  
 заполняет Возвращает имя константы перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает, `S_FALSE` Если значение не имеет связанного имени, или возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 При наличии нескольких имен, связанных с одним и тем же значением, будет возвращено первое имя, определенное в перечислении.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
