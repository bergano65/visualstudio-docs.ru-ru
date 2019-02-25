---
title: IDebugProperty3::DestroyObjectID | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 540427286306999b25fba99a2efbd17013740d90
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708996"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Уничтожает уникальный идентификатор, связанный с этим свойством, указывающее, что вызывающий объект больше не волнует для определения этого свойства уникально от всех других свойств.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если модуль отладки не требуется для поддержки уникальных идентификаторов для свойства (так как он уже отслеживает их однозначно внутренне), а затем может просто вернуть `E_NOTIMPL` для этого метода.

 Уникальные идентификаторы, созданные с помощью вызова [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) метод, когда вызывающий объект хочет убедиться, что это свойство однозначно идентифицируется среди всех остальных свойств.

## <a name="see-also"></a>См. также
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)