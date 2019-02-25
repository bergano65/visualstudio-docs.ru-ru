---
title: IDebugProperty2::GetReference | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: abff655b41dbc55735b7dea2934f7d396aae5f4c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698122"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Возвращает ссылку на значение свойства.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetReference(
   IDebugReference2** ppReference
);
```

```csharp
int GetReference(
   out IDebugReference2 ppReference
);
```

#### <a name="parameters"></a>Параметры
 `ppRererence`

 [out] Возвращает [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, представляющий ссылку на значение свойства.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки, обычно `E_NOTIMPL` или `E_GETREFERENCE_NO_REFERENCE`.

## <a name="see-also"></a>См. также
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)