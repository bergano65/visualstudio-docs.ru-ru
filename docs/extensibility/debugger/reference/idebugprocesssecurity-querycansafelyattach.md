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
ms.openlocfilehash: 891a0c200b02f8768ef68d1d87649bfd35cf59d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917542"
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