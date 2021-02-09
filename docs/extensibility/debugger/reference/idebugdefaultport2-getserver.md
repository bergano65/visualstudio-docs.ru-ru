---
title: 'IDebugDefaultPort2:: Server | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::GetServer
helpviewer_keywords:
- IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e046dbad9329ae377cef6864b7bc71b2ea6a538b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894950"
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Этот метод получает интерфейс к серверу, на котором включен этот порт.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetServer(
   IDebugCoreServer3** ppServer
);
```

```csharp
int GetServer(
   out IDebugCoreServer3 ppServer
);
```

## <a name="parameters"></a>Параметры
`ppServer`\
заполняет Возвращает объект, реализующий интерфейс [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) .

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) реализуется в Visual Studio и представляет сервер, на котором расположен порт.

## <a name="see-also"></a>См. также раздел
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
