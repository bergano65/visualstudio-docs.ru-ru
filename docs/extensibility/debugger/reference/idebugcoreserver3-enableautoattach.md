---
title: IDebugCoreServer3:EnableAutoAttach Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732911"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Позволяет автоматическое крепение для указанных двигателей отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Параметры
`rgguidSpecificEngines`\
(в) Массив GUIDs для каждого двигателя отладки, чтобы отметить как автоматическое присоединение.

`celtSpecificEngines`\
(в) Количество двигателей, `rgguidSpecificEngines`указанных в .

`pszStartPageUrl`\
(в) Стартовый URL для использования при автоматическом подключении.

`pbstrSessionID`\
(ваут) Идентификатор сеанса, который был автоматически прикреплен.

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае возвращает код ошибки. Один код `E_AUTO_ATTACH_NOT_REGISTERED`ошибки, который указывает, что фабрика класса авто-атташе не была зарегистрирована.

## <a name="remarks"></a>Примечания
 При запуска программы, связанной с указанным URL, указанные двигатели отладки автоматически запускаются и прикрепляются.

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
