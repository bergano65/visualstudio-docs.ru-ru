---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e718efddc90c45ced7e497a9c66c9ab3889c090
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311427"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Этот метод позволяет поставщика порта отображать предупреждение перед пользователь присоединяет к процессу unsafe.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращаемые значения, как показано ниже:

- `S_OK`: Присоединение к процессу, безопасно и отображается диалоговое окно без предупреждения.

- `S_FALSE`: Присоединение может не быть проблемой безопасности и отображается диалоговое окно с предупреждением.

- `FAILURE`: Присоединение к процессу, завершится ошибкой.

## <a name="see-also"></a>См. также
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)