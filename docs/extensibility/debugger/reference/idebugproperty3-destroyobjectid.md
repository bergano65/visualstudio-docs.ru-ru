---
title: IDebugProperty3::D Естройобжектид | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6afc0f5243d9f50f2d777c0bd43e6bba1de5e495
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936110"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Уничтожает уникальный идентификатор, связанный с этим свойством, который указывает, что вызывающий объект более не должен идентифицировать это свойство, уникально на основе всех остальных свойств.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Если модулю отладки не требуется поддерживать уникальные идентификаторы для свойства (поскольку он уже отслеживает их уникальным образом), то он может просто вернуться `E_NOTIMPL` для этого метода.

 Уникальные идентификаторы создаются с помощью вызова метода [креатеобжектид](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) , когда вызывающему объекту нужно убедиться, что это свойство однозначно идентифицируется всеми другими свойствами.

## <a name="see-also"></a>См. также раздел
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
