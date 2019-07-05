---
title: IDebugCoreServer3::EnableAutoAttach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9eb8beed7f32e9c6fb64212f73a41a35544259bb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326976"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Включает автоматическое присоединение для указанного отладчики.

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
[in] Массив идентификаторов GUID для каждого ядра отладки, чтобы пометить как автоматическое присоединение.

`celtSpecificEngines`\
[in] Число ядер, указанный в `rgguidSpecificEngines`.

`pszStartPageUrl`\
[in] Начальный URL-адрес для использования при присоединении автоматически.

`pbstrSessionID`\
[out] Идентификатор сеанса, который был подключен автоматически.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Один код ошибки- `E_AUTO_ATTACH_NOT_REGISTERED`, который указывает, что фабрика класса auto-attach не был зарегистрирован.

## <a name="remarks"></a>Примечания
 При запуске программы, связанный с указанным URL-адрес, указанный отладчики автоматически к работе и подключен.

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)