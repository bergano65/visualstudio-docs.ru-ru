---
title: DEBUG_REASON | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737423"
---
# <a name="debug_reason"></a>DEBUG_REASON
Указывает, почему процесс был запущен для отладки.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>Поля
`DEBUG_REASON_ERROR`\
Произошла неспецифическая ошибка (используется в качестве условия по умолчанию, если по каким-либо причинам не подходит).

`DEBUG_REASON_USER_LAUNCHED`\
Процесс был запущен по запросу пользователя.

`DEBUG_REASON_USER_ATTACHED`\
Этот уже запущенный процесс был подключен пользователем.

`DEBUG_REASON_AUTO_ATTACHED`\
Процесс был автоматически присоединен к моменту запуска.

`DEBUG_REASON_CAUSALITY`\
Процесс был запущен из-за JIT *-события* отладки.

## <a name="remarks"></a>Remarks
Возвращается методом [жетдебугреасон](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
