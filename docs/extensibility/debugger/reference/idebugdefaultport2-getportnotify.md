---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7e0cc45ba3f692f799deb568bcbb84cc5edf7bf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712519"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Этот метод возвращает [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) интерфейс для этого порта.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetPortNotify(
   IDebugPortNotify2** ppPortNotify
);
```

```csharp
int GetPortNotify(
   out IDebugPortNotify2 ppPortNotify
);
```

#### <a name="parameters"></a>Параметры
 `ppPortNotify`

 [out] [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) объекта.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Как правило `QueryInterface` метод вызывается для объекта, реализующего [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс для получения [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) интерфейс. Тем не менее существуют обстоятельства, в которых реализуется требуемого интерфейса на другой объект. Этот метод скрывает условиях и возвращает `IDebugPortNotify2` из наиболее подходящего объекта.

## <a name="see-also"></a>См. также
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)