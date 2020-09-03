---
title: 'Идебугпроцесссекурити:: Куерикансафеляттач | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723208"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Этот метод позволяет поставщику порта отображать предупреждение перед присоединением пользователя к незащищенному процессу.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Возвращаемое значение
 Ниже приведены возвращаемые значения.

- `S_OK`: Присоединение к процессу является надежным, и не отображается диалоговое окно предупреждения.

- `S_FALSE`: Присоединение может быть проблемой безопасности, и отображается диалоговое окно с предупреждением.

- `FAILURE`: Присоединение к процессу завершается ошибкой.

## <a name="see-also"></a>См. также раздел
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
