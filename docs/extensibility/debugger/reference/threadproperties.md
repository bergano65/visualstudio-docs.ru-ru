---
title: THREADPROPERTIES | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4079c688358f3e7deedd28b5eb05e556192bfe6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="threadproperties"></a>THREADPROPERTIES
Описание свойств потока.  
  
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
 dwFields  
 Сочетание флагов из [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) перечисление, описывающее, какие поля в этой структуры являются допустимыми.  
  
 dwThreadId  
 Идентификатор потока.  
  
 dwSuspendCount  
 Число приостановок потока.  
  
 dwThreadState  
 Значение из [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) перечисление, указывающее состояние работы потока.  
  
 bstrPriority  
 Строка, указывающая приоритет потока; Например «Выше среднего», «Normal» или «Критические времени».  
  
 bstName  
 Имя потока.  
  
 bstrLocation  
 Расположение потока (обычно верхний кадр стека), обычно выраженное как имя метода, где выполнение приостановлено.  
  
## <a name="remarks"></a>Примечания  
 Эта структура заполняется с помощью вызова [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) метод. Таким образом возвращенные сведения обычно используется в заполнении **потоков** окна.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)