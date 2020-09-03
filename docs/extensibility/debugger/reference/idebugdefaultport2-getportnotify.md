---
title: 'IDebugDefaultPort2:: Жетпортнотифи | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
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
заполняет Объект [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Как правило, `QueryInterface` метод вызывается для объекта, реализующего интерфейс [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , чтобы получить интерфейс [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) . Однако существуют обстоятельства, в которых требуемый интерфейс реализуется на другом объекте. Этот метод скрывает эти обстоятельства и возвращает `IDebugPortNotify2` интерфейс из наиболее подходящего объекта.

## <a name="see-also"></a>См. также раздел
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
