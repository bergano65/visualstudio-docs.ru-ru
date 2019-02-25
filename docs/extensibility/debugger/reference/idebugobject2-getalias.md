---
title: IDebugObject2::GetAlias | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d08d9108ed4a433bcbcb17d6d4587532542b303
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719851"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
Возвращает псевдоним, связанный с данным объектом, если таковые имеются.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetAlias(
   IDebugAlias** ppAlias
);
```

```csharp
int GetAlias(
   out IDebugAlias ppAlias
);
```

#### <a name="parameters"></a>Параметры
 `ppAlias`

 [out] Возвращает [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) объект, представляющий псевдоним для этого объекта; в противном случае возвращает значение null.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Псевдоним для объекта создается с помощью вызова [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) метод.

## <a name="see-also"></a>См. также
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)