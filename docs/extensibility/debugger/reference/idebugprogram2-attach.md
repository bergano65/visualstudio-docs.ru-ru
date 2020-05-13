---
title: IDebugProgram2::Прикрепите Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723133"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Прикрепляется к программе.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>Параметры
`pCallback`\
(в) Объект [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) который будет использоваться для уведомления о событиях.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны некоторые возможные коды ошибок.

|Значение|Описание|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанная программа уже прикреплена к отладчику.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Нарушение безопасности произошло во время процедуры присоединения.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|К отладчику не может быть прикреплена настольная программа.|

## <a name="remarks"></a>Примечания
 Отладочная движок (DE) никогда не вызывает этот метод для присоединения к программе. Если DE работает в адресном пространстве программы, называется метод [OnAttach.](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Если DE выполняется в пространстве адреса диспетчера сеанса (SDM), вызывается метод [Присоединения.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
