---
title: THREADPROPERTY_FIELDS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b181cc341ea0297cc78c0970a5de64df830dc3e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937539"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
Указывает, какие сведения о потоке требуется получить.  
  
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
  
## <a name="members"></a>Участники  
 TPF_ID  
 Инициализация и использование `dwThreadId` поле [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры.  
  
 TPF_SUSPENDCOUNT  
 Инициализация и использование `dwSuspendCount` поле `THREADPROPERTIE`структура.  
  
 TPF_STATE  
 Инициализация и использование `dwThreadState` поле `THREADPROPERTIE`структура.  
  
 TPF_PRIORITY  
 Инициализация и использование `bstrPriority` поле `THREADPROPERTIE`структура.  
  
 TPF_NAME  
 Инициализация и использование `bstrName` поле `THREADPROPERTIE`структура.  
  
 TPF_LOCATION  
 Инициализация и использование `bstrLocation` поле `THREADPROPERTIE`структура.  
  
 TPF_ALLFIELDS  
 Указывает все поля.  
  
## <a name="remarks"></a>Примечания  
 Эти значения передаются в качестве аргумента [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md) метод, чтобы указать, какие поля [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) структуры должны быть инициализированы.  
  
 Эти значения также используются в `dwFields` членом `THREADPROPERTIES` структура указывает, какие поля используются и допустимым.  
  
 Эти флаги могут быть объединены с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)