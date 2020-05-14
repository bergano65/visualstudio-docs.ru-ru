---
title: ТИП СООБЩЕНИЯ Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b4d0fd12495a59427500c16ef6f37d9f8b6e61f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714488"
---
# <a name="messagetype"></a>MESSAGETYPE
Упоняет тип и причину сообщения.

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

## <a name="fields"></a>Поля
 `MT_OUTPUTSTRING`\
 Означает, что сообщение должно быть отправлено в окно вывода. Это взаимоисключающие от `MT_MESSAGEBOX`.

 `MT_MESSAGEBOX`\
 Означает, что сообщение должно отображаться в поле сообщения. Это взаимоисключающие от `MT_OUTPUTSTRING`.

 `MT_TYPE_MASK`\
 Значение маски для изоляции пункта назначения для сообщения.

 `MT_REASON_EXCEPTION`\
 Означает, что окно сообщения отображается в результате исключения. Это взаимоисключающие от `MT_REASON_TRACEPOINT`.

 `MT_REASON_TRACEPOINT`\
 Означает, что окно сообщения отображается в результате попадания в точку трассировки. Это взаимоисключающие . `MT_REASON_EXCEPTION`

 `MT_REASON_MASK`\
 Значение маски для изоляции причины отображаемого сообщения.

## <a name="remarks"></a>Примечания
 Эти значения возвращаются из методов [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) и [GetErrorMessage.](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

 Одна из причин, по которой значения могут быть объединены с `OR`одним из значений назначения вывода с помощью bitwise.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)
- [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
