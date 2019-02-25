---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44b125f44f3345e7bd28a9993a7a44be2e378b53
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701437"
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

-   `S_OK`: Присоединение к процессу, безопасно и отображается диалоговое окно без предупреждения.

-   `S_FALSE`: Присоединение может не быть проблемой безопасности и отображается диалоговое окно с предупреждением.

-   `FAILURE`: Присоединение к процессу, завершится ошибкой.

## <a name="see-also"></a>См. также
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)