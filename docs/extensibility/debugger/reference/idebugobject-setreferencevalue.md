---
title: IDebugObject::SetReferenceValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e861a67ada36bd25b30e08bf8a62163bceea979
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211300"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Задает значения этого объекта ссылки.

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
[in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект, представляющий новое значение ссылки.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Этот метод выполняет это [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ссылка на объект на значение объекта, указанного в `pObject` параметра, извлекайте любой предыдущей ссылке. Обратите внимание, это `IDebugObject` объект уже должен быть ссылочным типом.

## <a name="see-also"></a>См. также
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)