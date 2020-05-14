---
title: IDebugDefaultPort2::GetServer Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3dbe6d813b85865b0fdbc20296473684203a3f1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732381"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Этот метод получает интерфейс на сервер, на который находится этот порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Параметры
`ppServer`\
(ваут) Возвращает объект, реализующий интерфейс [IDebugCoreServer3.](../../../extensibility/debugger/reference/idebugcoreserver3.md)

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) реализован Visual Studio и представляет сервер, на который расположен порт.

## <a name="see-also"></a>См. также
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
