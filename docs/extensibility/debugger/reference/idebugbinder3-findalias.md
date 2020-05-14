---
title: IDebugBinder3::FindAlias Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735861"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Этот метод находит псевдоним, данный имя. Это будет искать все псевдонимы в программе.

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
(в) Имя псевдонима, чтобы найти.

`ppAlias`\
(ваут) Псевдоним найден (если таков) представлен интерфейсом [IDebugAlias.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="return-value"></a>Возвращаемое значение
 В случае `S_OK`успеха, возвращается ; в противном случае, возвращает `S_FALSE` (если псевдоним не найден) или код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод инициализирует объект назначения, чтобы сматить перед вызовом; после этого оно испытывает для null значения потом для того чтобы обусловить был ли или не псевдоним был найден.

## <a name="see-also"></a>См. также
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
