---
title: CONNECTION_PROTOCOL Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737648"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Указывает протокол, используемый для связи между сервером отладки и пакетом отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Поля
`CONNECTION_NONE`\
Подключение к серверу не установлено.

`CONNECTION_UNKNOWN`\
Соединение было сделано, но оно неизвестного типа.

`CONNECTION_LOCAL`\
Подключение к локальному серверу.

`CONNECTION_PIPE`\
Соединение происходит через именованные трубы.

`CONNECTION_TCPIP`\
Соединение использует TCP/IP.

`CONNECTION_HTTP`\
Соединение использует HTTP (через веб-сервер).

`CONNECTION_OTHER`\
Установлен другой тип соединения (это значение в настоящее время не используется).

## <a name="remarks"></a>Примечания
Эти значения возвращаются из метода [GetConnectionProtocol.](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
