---
title: MESSAGETYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16d2b9ae9c446d4c8082a8c35c9e4d1810233b95
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687514"
---
# <a name="messagetype"></a>MESSAGETYPE
Указывает тип сообщения и причины.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
typedef DWORD MESSAGETYPE;
```

```csharp
public enum enum_MESSAGETYPE { 
   MT_OUTPUTSTRING      = 0x0000001,
   MT_MESSAGEBOX        = 0x00000002,
   MT_TYPE_MASK         = 0x000000FF,
   MT_REASON_EXCEPTION  = 0x00000100,
   MT_REASON_TRACEPOINT = 0x00000200,
   MT_REASON_MASK       = 0x0000FF00
};
```

## <a name="members"></a>Участники
 MT_OUTPUTSTRING указывает, что должно быть отправлено сообщение в окно вывода. Это взаимно исключают друг друга из `MT_MESSAGEBOX`.

 MT_MESSAGEBOX указывает, что сообщение должно отображаться в окне сообщения. Это взаимно исключают друг друга из `MT_OUTPUTSTRING`.

 Значение маски MT_TYPE_MASK объект для изоляции назначения для сообщения.

 MT_REASON_EXCEPTION указывает, что окно сообщения отображается из-за исключения. Это взаимно исключают друг друга из `MT_REASON_TRACEPOINT`.

 MT_REASON_TRACEPOINT указывает, что окно сообщения отображается в результате обращения к точке трассировки. Это взаимно исключают друг друга для `MT_REASON_EXCEPTION`.

 Значение маски MT_REASON_MASK объект для изоляции причина для отображаемого сообщения.

## <a name="remarks"></a>Примечания
 Эти значения возвращаются из [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) и [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) методы.

 Одно из значений причина могут сочетаться с одним из значений назначения выходных данных при помощи побитовой `OR`.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)