---
title: IdebugEnumfield:GetvalueFromStringCaseНечувствительные (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730253"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Этот метод использует нечувствительный к случаям поиск для возврата значения, связанного с именем константы перечисления.

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
(в) Строка, определяющая имя, для которого можно получить значение. Обратите внимание, что для СЗ это широкая строка символов.

`pValue`\
(ваут) Возвращает связанное числовое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращается, `S_FALSE`если имя не является частью перечисления или кодом ошибки.

## <a name="remarks"></a>Примечания
 Этот метод нечувствителен. Если необходим поиск, чувствительный к случаям (например, на таком языке, как СЗ, где имена чувствительны к случаям), используйте [GetValueFromString.](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)

## <a name="see-also"></a>См. также
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
