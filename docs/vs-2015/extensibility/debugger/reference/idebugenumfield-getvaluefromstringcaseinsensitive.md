---
title: 'Идебуженумфиелд:: Жетвалуефромстрингкасеинсенситиве | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efe94a721c432cb1284df299ca267271ab5bef4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188931"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод использует поиск с учетом регистра для возврата значения, связанного с именем константы перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszValue`  
 окне Строка, указывающая имя, для которого необходимо получить значение. Обратите внимание, что для C++ это строка расширенных символов.  
  
 `pValue`  
 заполняет Возвращает связанное числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение `S_OK` ; в противном случае возвращает значение `S_FALSE` , если имя не является частью перечисления, или код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод не учитывает регистр. Если требуется поиск с учетом регистра (например, на языке C++, где в именах учитывается регистр), используйте [жетвалуефромстринг](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>См. также:  
 [идебуженумфиелд](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
