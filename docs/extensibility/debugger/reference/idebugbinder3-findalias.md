---
title: 'IDebugBinder3:: Финдалиас | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1bac818844b69018bb9dc6a970a5659513dbe50d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925085"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Этот метод находит псевдоним по заданному имени. При этом будут искаться все псевдонимы в программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Параметры
`pcstrName`\
окне Имя искомого псевдонима.

`ppAlias`\
заполняет Найден псевдоним (если имеется), представленный интерфейсом [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) .

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает значение `S_FALSE` (если псевдоним не найден) или код ошибки.

## <a name="remarks"></a>Remarks
 Этот метод инициализирует целевой объект до значения null перед вызовом метода; После этого проверяется наличие значения NULL, чтобы определить, был ли найден псевдоним.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
