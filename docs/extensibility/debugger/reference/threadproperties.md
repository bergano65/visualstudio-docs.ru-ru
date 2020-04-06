---
title: THREADPROPERTIES (АНГЛ. Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0ed4e33b1f8e0e905f3c88493c9f513c177fbc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713423"
---
# <a name="threadproperties"></a>THREADPROPERTIES
Описывает свойства потока.

## <a name="syntax"></a>Синтаксис

```cpp
typedef struct _tagTHREADPROPERTIES { 
   THREADPROPERTY_FIELDS dwFields;
   DWORD                 dwThreadId;
   DWORD                 dwSuspendCount;
   DWORD                 dwThreadState;
   BSTR                  bstrPriority;
   BSTR                  bstrName;
   BSTR                  bstrLocation;
} THREADPROPERTIES;
```

```csharp
public struct THREADPROPERTIES { 
   public uint   dwFields;
   public uint   dwThreadId;
   public uint   dwSuspendCount;
   public uint   dwThreadState;
   public string bstrPriority;
   public string bstrName;
   public string bstrLocation;
};
```

## <a name="members"></a>Участники
 `dwFields`\
 Комбинация флагов из [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) перечисления, описывающая, какие поля в этой структуре являются действительными.

 `dwThreadId`\
 Идентификатор нити.

 `dwSuspendCount`\
 Поток приостанавливает подсчет.

 `dwThreadState`\
 Значение из перечисления [THREADSTATE,](../../../extensibility/debugger/reference/threadstate.md) указывающее состояние рабочего потока.

 `bstrPriority`\
 Строка, определяющая приоритет потока; например, "Выше нормы", "Нормальный" или "Критические моменты".

 `bstName`\
 Имя потока.

 `bstrLocation`\
 Местоположение потока (обычно верхняя рамка стека), обычно выраженное как название метода, где выполнение в настоящее время остановлено.

## <a name="remarks"></a>Примечания
 Эта структура заполняется вызовом к методу [GetThreadProperties.](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) Используемая таким образом информация обычно используется при заполнении окна **потоков.**

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
