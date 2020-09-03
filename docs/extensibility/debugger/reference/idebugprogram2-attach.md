---
title: 'IDebugProgram2:: Attach | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723133"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Присоединяется к программе.

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
окне Объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , используемый для уведомления о событии отладки.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны некоторые возможные коды ошибок.

|Значение|Описание|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанная программа уже подключена к отладчику.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Во время процедуры подключения возникло нарушение безопасности.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Невозможно присоединить к отладчику программу для настольных систем.|

## <a name="remarks"></a>Remarks
 Модуль отладки (DE) никогда не вызывает этот метод для присоединения к программе. Если в адресном пространстве программы выполняется DE, вызывается метод [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) . Если выполняется DE в адресном пространстве диспетчера отладки сеансов (SDM), вызывается метод [attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>См. также раздел
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
