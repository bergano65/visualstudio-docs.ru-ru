---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59f1917f420e4815bcd525f131e4b524e53e6b3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347321"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Извлекает сведения о группе символов, членом которой является поставщик символов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetCurrentModulesState(
    DWORD*          pState,
    unsigned long * count
);
```

```csharp
int GetCurrentModulesState(
    out uint pState,
    out uint count
);
```

## <a name="parameters"></a>Параметры
`pState`\
[out] Состояние группы поставщика символов.

`count`\
[out] Число модулей в группе.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Состояние изменяется каждый раз, когда модуль добавлен или удален из группы символов. Таким образом этот метод может использоваться для обнаружения, если был изменен группу символов.

## <a name="see-also"></a>См. также
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)