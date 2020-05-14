---
title: IDebugEnumfield:GetValueFromString Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb340721c9f446b740c2723dc3f6dc05452e74de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730260"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Этот метод возвращает значение, связанное с именем константы перечисления.

## <a name="syntax"></a>Синтаксис

```cpp
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

## <a name="parameters"></a>Параметры
`pszValue`\
(в) Строка, определяющая имя, для которого можно получить значение. Обратите внимание, что для СЗ это широкая строка символов.

`pValue`\
(ваут) Возвращает связанное числовое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращается, `S_FALSE`если имя не является частью перечисления или кодом ошибки.

## <a name="remarks"></a>Примечания
 Этот метод является чувствительным к случаям. Если необходим поиск без чувствительного к случаям (например, на таком языке, как Visual Basic, где имена не чувствительны к делу), используйте [GetValueFromStringCaseInsensitive.](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)

## <a name="see-also"></a>См. также
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
