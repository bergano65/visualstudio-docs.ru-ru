---
title: IDebugEnumField::GetValueFromString | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f553b7f019dd89af771e057a46a11b1affed1308
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993327"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает значение, связанное с именем константы перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszValue`  
 [in] Строка, указывающая имя, для которого следует получить значение. Обратите внимание на то, что для C++, это строку расширенных символов.  
  
 `pValue`  
 [out] Возвращает соответствующее числовое значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE`, если имя не является частью перечисление, или код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не учитывает регистр. Не учитывать регистр при необходимости (например, в языке, как Visual Basic, где имена не учитывается регистр), используйте [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>См. также  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
