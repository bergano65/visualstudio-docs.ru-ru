---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2b0185b0c3f7f26cfe9ffa8806c5049af323c517
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614953"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Этот метод осуществляет поиск псевдоним, заданному имени. Таким образом, найти все псевдонимы в программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

## <a name="parameters"></a>Параметры
`pcstrName`\
[in] Имя псевдонима для поиска.

`ppAlias`\
[out] Представленный псевдоним, найденный (если таковые имеются) [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` (Если псевдоним не найден) или код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод инициализирует в целевой объект, значение null перед вызовом метода; Затем проверяется значение null, впоследствии определить, был ли найден псевдоним.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)