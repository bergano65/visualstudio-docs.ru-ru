---
title: THREADPROPERTY_FIELDS Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b31c43187d1136f7a194c42749c430de6cd064a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713400"
---
# <a name="threadproperty_fields"></a>THREADPROPERTY_FIELDS
Определяет, какая информация о потоке должна быть извлечена.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
typedef DWORD THREADPROPERTY_FIELDS;
```

```csharp
public enum enum_THREADPROPERTY_FIELDS { 
   TPF_ID           = 0x0001,
   TPF_SUSPENDCOUNT = 0x0002,
   TPF_STATE        = 0x0004,
   TPF_PRIORITY     = 0x0008,
   TPF_NAME         = 0x0010,
   TPF_LOCATION     = 0x0020,
   TPF_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Поля
 `TPF_ID`\
 Инициализация/использование `dwThreadId` поля структуры [THREADPROPERTIES.](../../../extensibility/debugger/reference/threadproperties.md)

 `TPF_SUSPENDCOUNT`\
 Инициализация/использование `dwSuspendCount` `THREADPROPERTIE`поля структуры S.

 `TPF_STATE`\
 Инициализация/использование `dwThreadState` `THREADPROPERTIE`поля структуры S.

 `TPF_PRIORITY`\
 Инициализация/использование `bstrPriority` `THREADPROPERTIE`поля структуры S.

 `TPF_NAME`\
 Инициализация/использование `bstrName` `THREADPROPERTIE`поля структуры S.

 `TPF_LOCATION`\
 Инициализация/использование `bstrLocation` `THREADPROPERTIE`поля структуры S.

 `TPF_ALLFIELDS`\
 Определяет все поля.

## <a name="remarks"></a>Примечания
 Эти значения передаются в качестве аргумента методу [GetThreadProperties,](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) чтобы указать, какие поля структуры [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) должны быть инициализированы.

 Эти значения также используются `dwFields` в `THREADPROPERTIES` составе структуры для указания того, какие поля используются и действительны.

 Эти флаги могут быть `OR`объединены с bitwise .

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
