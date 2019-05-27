---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 163e675d0ef4b47e0a0bf82d730adcc081eddec3
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200096"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Этот метод использует поиск с учетом регистра для возврата значения, связанного с именем константы перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
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

## <a name="parameters"></a>Параметры
`pszValue`\
[in] Строка, указывающая имя, для которого следует получить значение. Обратите внимание на то, что для C++, это строку расширенных символов.

`pValue`\
[out] Возвращает соответствующее числовое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE`, если имя не является частью перечисление, или код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод не учитывает регистр. Если регистр при поиске необходимо (например, в языке, как C++, где в именах учитывается регистр), используйте [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>См. также
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)