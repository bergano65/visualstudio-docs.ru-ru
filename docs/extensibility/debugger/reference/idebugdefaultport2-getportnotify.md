---
title: IDebugDefaultPort2::GetPortNotify Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 670dd128e6962c1e1d12f81eea03f9759fa56621
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732406"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Этот метод получает интерфейс [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) для этого порта.

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

## <a name="parameters"></a>Параметры
`ppPortNotify`\
(ваут) Объект [IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md)

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Обычно `QueryInterface` метод вызывается на объект, реализующий интерфейс [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) для получения интерфейса [IDebugPortNotify2.](../../../extensibility/debugger/reference/idebugportnotify2.md) Однако существуют обстоятельства, при которых желаемый интерфейс реализуется на другом объекте. Этот метод скрывает эти обстоятельства `IDebugPortNotify2` и возвращает интерфейс от наиболее подходящего объекта.

## <a name="see-also"></a>См. также
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
