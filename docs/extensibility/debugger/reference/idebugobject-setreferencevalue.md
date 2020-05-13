---
title: IDebugObject::SetReferenceValue Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726376"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Устанавливает эталонное значение этого объекта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Параметры
`pObject`\
(в) Объект [IDebugObject,](../../../extensibility/debugger/reference/idebugobject.md) представляющий новое эталонное значение.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод делает этот объект [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ссылкой на `pObject` значение объекта, приведенного в параметре, выбрасывая любую предыдущую ссылку. Обратите внимание, что этот `IDebugObject` объект уже должен быть эталонным типом.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
