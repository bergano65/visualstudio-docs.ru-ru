---
title: IDebugПроцессБезопасность::КвикКонСейтлиПритс (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723208"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Этот метод позволяет поставщику порта отображать предупреждение до того, как пользователь прикрепится к небезопасному процессу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Возвращаемое значение
 Значения возврата следующие:

- `S_OK`: Присоединение к процессу является безопасным и не отображается предупреждающий диалоговый ящик.

- `S_FALSE`: Присоединение может быть проблемой безопасности и диалоговая будка с предупреждением отображается.

- `FAILURE`: Присоединение к процессу не удается.

## <a name="see-also"></a>См. также
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
