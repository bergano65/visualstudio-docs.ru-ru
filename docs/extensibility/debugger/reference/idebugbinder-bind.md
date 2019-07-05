---
title: IDebugBinder::Bind | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00d7e63b8a521ee25d2c7d378aeb82d064358ec9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344496"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Этот метод получает контекст в памяти или объект, содержащий текущее значение символа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Параметры
`pContainer`\
[in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , содержащая дочерние ссылается `pField`.

`pField`\
[in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , представляющий символ.

`ppObject`\
[out] Возвращает `IDebugObject` , представляющий экземпляр символа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)