---
title: IDebugCoreServer3::EnableAutoAttach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c1bf5f210d9b37b35d43a393a25b1c9df44a7e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875890"
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

#### <a name="parameters"></a>Параметры
 `rgguidSpecificEngines`

 [in] Массив идентификаторов GUID для каждого ядра отладки, чтобы пометить как автоматическое присоединение.

 `celtSpecificEngines`

 [in] Число ядер, указанный в `rgguidSpecificEngines`.

 `pszStartPageUrl`

 [in] Начальный URL-адрес для использования при присоединении автоматически.

 `pbstrSessionID`

 [out] Идентификатор сеанса, который был подключен автоматически.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Один код ошибки- `E_AUTO_ATTACH_NOT_REGISTERED`, который указывает, что фабрика класса auto-attach не был зарегистрирован.

## <a name="remarks"></a>Примечания
 При запуске программы, связанный с указанным URL-адрес, указанный отладчики автоматически к работе и подключен.

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)