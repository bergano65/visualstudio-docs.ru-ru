---
title: IDebugCoreServer3::DiagnoseWebDebuggingОшибка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732948"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Попытки определить, почему сбой автоматического атташе.

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

## <a name="parameters"></a>Параметры
`pszUrl`\
(в) В настоящее время не используется; всегда должны быть установлены на нулевую стоимость.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Ниже приведены другие типичные коды возврата:

|Код|Описание|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Не удается определить, почему удаленный сервер не смог начать отладку.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Не удается отладить удаленный сервер, возможно, из-за недостаточного разрешения или из-за того, что глагол DEBUG не включен.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Веб-сервер заблокирован и блокирует глагол DEBUG, который необходим для включения отладки.|

## <a name="see-also"></a>См. также
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
