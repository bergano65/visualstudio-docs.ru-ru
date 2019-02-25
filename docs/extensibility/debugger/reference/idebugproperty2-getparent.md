---
title: IDebugProperty2::GetParent | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30fa28ba52d40698447c6607be4b694466bb6127
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680156"
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
Возвращает свойство родительского свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetParent ( 
   IDebugProperty2** ppParent
);
```

```csharp
int GetParent ( 
   out IDebugProperty2 ppParent
);
```

#### <a name="parameters"></a>Параметры
 `ppParent`

 [out] Возвращает [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) объект, представляющий родительский объект свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `S_GETPARENT_NO_PARENT` Если родительский элемент отсутствует.

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)