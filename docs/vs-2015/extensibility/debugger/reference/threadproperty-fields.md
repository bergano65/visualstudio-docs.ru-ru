---
title: THREADPROPERTY_FIELDS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc0e0f7cae4aed887809c22bda0cd6a9ed50307f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204809"
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает, какие сведения о потоке требуется получить.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)
