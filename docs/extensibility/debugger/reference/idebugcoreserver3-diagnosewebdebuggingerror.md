---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8173283adadd1290bdd83bf5f6810622efbff959
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722945"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Чтобы определить, почему auto-attach попыток.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

#### <a name="parameters"></a>Параметры
 `pszUrl`

 [in] Не используется; всегда должны устанавливаться в значение null.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Ниже приведены другие типичные коды возврата.

|Код|Описание:|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Не удается определить, почему удаленному серверу не удалось начать отладку.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Не удается выполнить отладку на удаленном сервере, из-за недостаточных разрешений или потому, что команда DEBUG не включена.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Веб-сервер заблокирован и блокирует команду DEBUG, который необходим для включения отладки.|

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)