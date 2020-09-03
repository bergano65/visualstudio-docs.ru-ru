---
title: СРЕАДПРОПЕРТИЕС | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
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
 Сочетание флагов из перечисления [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , описывающее, какие поля в этой структуре являются допустимыми.

 `dwThreadId`\
 Идентификатор потока.

 `dwSuspendCount`\
 Число приостановок потока.

 `dwThreadState`\
 Значение из перечисления "перечисление [", указывающее](../../../extensibility/debugger/reference/threadstate.md) состояние операционного потока.

 `bstrPriority`\
 Строка, указывающая приоритет потока; Например, "выше обычного", "нормального" или "критическое время".

 `bstName`\
 Имя потока.

 `bstrLocation`\
 Расположение потока (обычно самый верхний кадр стека), обычно выраженное в виде имени метода, в котором выполнение в данный момент останавливается.

## <a name="remarks"></a>Remarks
 Эта структура заполняется вызовом метода [жетсреадпропертиес](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Эти сведения обычно используются при заполнении окна **потоков** .

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)
- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
