---
title: "THREADPROPERTIES | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: THREADPROPERTIES
helpviewer_keywords: THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b4ec394deef3b317d91e6cbe22bbc1d95a6aca5e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
  
## <a name="members"></a>Члены  
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