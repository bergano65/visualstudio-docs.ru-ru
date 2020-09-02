---
title: 'Идебугаррайобжект:: @ Elements | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be06acbef93d8858557fea5bd7563168be2d28aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736239"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Возвращает перечислитель всех элементов массива.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Параметры
`ppEnum`\
заполняет Возвращает объект [иенумдебугобжектс](../../../extensibility/debugger/reference/ienumdebugobjects.md) , позволяющий перечислять все элементы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 В качестве альтернативы можно использовать методы [NOCOUNT](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) и- [элемента](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) для выполнения итерации по элементам.

## <a name="see-also"></a>См. также раздел
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
