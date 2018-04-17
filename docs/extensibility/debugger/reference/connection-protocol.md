---
title: CONNECTION_PROTOCOL | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1e1dc8cd22b529eafd6183578be7de6ffe69549
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Указывает протокол, используемой для связи между сервером отладки и отладочный пакет (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef enum tagCONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
} CONNECTION_PROTOCOL;  
```  
  
```csharp  
public enum CONNECTION_PROTOCOL {  
   CONNECTION_NONE    = 0,  
   CONNECTION_UNKNOWN = 1,  
   CONNECTION_LOCAL   = 2,  
   CONNECTION_PIPE    = 3,  
   CONNECTION_TCPIP   = 4,  
   CONNECTION_HTTP    = 5,  
   CONNECTION_OTHER   = 6  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 CONNECTION_NONE  
 Нет соединения с сервером.  
  
 CONNECTION_UNKNOWN  
 Установить соединение, но имеет неизвестный тип.  
  
 CONNECTION_LOCAL  
 Соединение предназначено для локального сервера.  
  
 CONNECTION_PIPE  
 Подключение осуществляется через именованный канал.  
  
 CONNECTION_TCPIP  
 Соединение использует протокол TCP/IP.  
  
 CONNECTION_HTTP  
 Соединение использует протокол HTTP (с помощью веб-сервера).  
  
 CONNECTION_OTHER  
 Было установлено соединение другого типа (это значение не используется в настоящее время).  
  
## <a name="remarks"></a>Примечания  
 Эти значения возвращаются из [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)