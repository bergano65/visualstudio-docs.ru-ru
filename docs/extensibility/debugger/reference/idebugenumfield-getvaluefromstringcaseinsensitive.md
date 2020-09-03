---
title: 'Идебуженумфиелд:: Жетвалуефромстрингкасеинсенситиве | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730253"
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
окне Строка, указывающая имя, для которого необходимо получить значение. Обратите внимание, что для C++ это строка расширенных символов.

`pValue`\
заполняет Возвращает связанное числовое значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает значение `S_OK` ; в противном случае возвращает значение `S_FALSE` , если имя не является частью перечисления, или код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод не учитывает регистр. Если требуется поиск с учетом регистра (например, на языке C++, где в именах учитывается регистр), используйте [жетвалуефромстринг](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>См. также раздел
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
