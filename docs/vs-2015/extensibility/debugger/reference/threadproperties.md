---
title: СРЕАДПРОПЕРТИЕС | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTIES
helpviewer_keywords:
- THREADPROPERTIES structure
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4815a1e42b98fba812e8a3c2a53516bff16081db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204824"
---
# <a name="threadproperties"></a>THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описывает свойства потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 двфиелдс  
 Сочетание флагов из перечисления [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) , описывающее, какие поля в этой структуре являются допустимыми.  
  
 двсреадид  
 Идентификатор потока.  
  
 двсуспендкаунт  
 Число приостановок потока.  
  
 двсреадстате  
 Значение из перечисления "перечисление [", указывающее](../../../extensibility/debugger/reference/threadstate.md) состояние операционного потока.  
  
 бстрприорити  
 Строка, указывающая приоритет потока; Например, "выше обычного", "нормального" или "критическое время".  
  
 бстнаме  
 Имя потока.  
  
 бстрлокатион  
 Расположение потока (обычно самый верхний кадр стека), обычно выраженное в виде имени метода, в котором выполнение в данный момент останавливается.  
  
## <a name="remarks"></a>Remarks  
 Эта структура заполняется вызовом метода [жетсреадпропертиес](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) . Эти сведения обычно используются при заполнении окна **потоков** .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [жетсреадпропертиес](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)
