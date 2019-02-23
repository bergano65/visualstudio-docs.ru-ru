---
title: IDebugField::GetContainer | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 283e23a70b95e3882569dbb18dda7ba365b8b765
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718148"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Этот метод возвращает контейнер поля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

#### <a name="parameters"></a>Параметры
 `ppContainerField`

 [out] Возвращает контейнер, представленные как [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) интерфейс.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если это поле не имеет контейнер, возвращенный `ppContainerField` будет иметь значение null.

## <a name="see-also"></a>См. также
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)