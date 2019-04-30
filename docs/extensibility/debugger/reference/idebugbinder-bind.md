---
title: IDebugBinder::Bind | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcb3535a2ace5818664a34a5d7b818d7dfd8b025
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877576"
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

#### <a name="parameters"></a>Параметры
 `pContainer`

 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , содержащая дочерние ссылается `pField`.

 `pField`

 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , представляющий символ.

 `ppObject`

 [out] Возвращает `IDebugObject` , представляющий экземпляр символа.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)