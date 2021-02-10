---
title: Идебугалиас::D Dispose | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 033d74be9548b6bdaaccfe567e99c1d94453bca5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944801"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Помечает этот псевдоним для удаления.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 После вызова этого метода псевдоним будет недоступен.

## <a name="see-also"></a>См. также раздел
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
