---
title: "CONNECTION_PROTOCOL | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ed80d3caee3a0e407e42670adcabb0e2710bd59d
ms.lasthandoff: 02/22/2017

---
# <a name="connectionprotocol"></a>CONNECTION_PROTOCOL
Указывает протокол, используемый для обмена данными между сервером отладки и отладки пакета (DE).  
  
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
  
```c#  
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
 Подключение установлено, но оно имеет неизвестный тип.  
  
 CONNECTION_LOCAL  
 Подключен к локальному серверу.  
  
 CONNECTION_PIPE  
 Подключение осуществляется через именованный канал.  
  
 CONNECTION_TCPIP  
 Соединение использует протокол TCP/IP.  
  
 CONNECTION_HTTP  
 Соединение использует протокол HTTP (через веб-сервер).  
  
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
