---
title: 'Идебугбиндер:: Ресолверунтиметипе | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dad51c2741296f9d666a352a5e5a6aa0a3e9cf61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938230"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Этот метод определяет тип времени выполнения объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Параметры
`pObject`\
окне [Идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , который необходимо разрешить.

`ppResolved`\
заполняет Возвращает тип объекта в виде [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Тип времени выполнения объекта не всегда известен во время компиляции. Например, с помощью полиморфизма аргумент может быть передан в функцию в качестве базового класса, например класса Button. Фактический аргумент может быть производным классом, например классом переключателя.

## <a name="see-also"></a>См. также раздел
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
