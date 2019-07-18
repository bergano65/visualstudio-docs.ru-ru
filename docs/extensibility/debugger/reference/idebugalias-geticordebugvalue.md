---
title: IDebugAlias::GetICorDebugValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8ef27f9af5626b716339281c010c62c2515fb8b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746844"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Извлекает интерфейс управляемого кода, который представляет значение, связанное с данным псевдонимом.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Параметры
`ppUnk`\
[out] `IUnknown` интерфейс, который представляет значение, связанное с данным псевдонимом. Этот интерфейс может запрашиваться для `ICorDebugValue` интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод применим только к значениям управляемых ( `ICorDebugValue` является интерфейсом, доступных в .NET Framework и определен в пакете SDK для .NET Framework в файле CorDebug.IDL).

## <a name="see-also"></a>См. также
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)