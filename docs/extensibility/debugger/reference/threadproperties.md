---
title: THREADPROPERTIES | Документация Майкрософт
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
ms.openlocfilehash: 14db7869717a2edf1ac64be744ab1f6058455c1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845320"
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
 dwFields  
 Сочетание флагов из [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) перечисление, описывающее, какие поля в этой структуре являются допустимыми.  
  
 dwThreadId  
 Идентификатор потока.  
  
 dwSuspendCount  
 Число приостановок потока.  
  
 dwThreadState  
 Значение из [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) перечисление, указывающее состояние работы потока.  
  
 bstrPriority  
 Строка, указывающая приоритет потока; Например «Выше среднего», «Normal» или «Critical времени».  
  
 bstName  
 Имя потока.  
  
 bstrLocation  
 Расположение потока (обычно верхний кадр стека), обычно выраженное как имя метода, где выполнение приостановлено.  
  
## <a name="remarks"></a>Примечания  
 Эта структура заполняется с помощью вызова [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) метод. Сведения, поэтому возвращаемые обычно используется при заполнении **потоков** окна.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)