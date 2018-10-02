---
title: BPREQI_FIELDS | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4be4e49b79c2b2dc62843e785d1fb38b517f34b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573096"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [BPREQI_FIELDS](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bpreqi-fields).  
  
Указывает сведения, которые требуется получить о запросе точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Участники  
 BPREQI_BPLOCATION  
 Инициализация и использование `bpLocation` поле (точки останова) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) или [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 BPREQI_LANGUAGE  
 Инициализация и использование `guidLanguage` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_PROGRAM  
 Инициализация и использование `pProgram` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_PROGRAMNAME  
 Инициализация и использование `bstrProgramName` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_THREAD  
 Инициализация и использование `pThread` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_THREADNAME  
 Инициализация и использование `bstrThreadName` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_PASSCOUNT  
 Инициализация и использование `bpPassCount` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_CONDITION  
 Инициализация и использование `bpCondition` поле (условие точки останова) `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_FLAGS  
 Инициализация и использование `dwFlags` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_ALLOLDFIELDS  
 Все поля для инициализации и использование объекта `BP_REQUEST_INFO` структуры.  
  
 BPREQI_VENDOR  
 Инициализация и использование `guidVendor` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_CONSTRAINT  
 Инициализация и использование `bstrConstraint` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_TRACEPOINT  
 Инициализация и использование `bstrTracepoint` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI_ALLFIELDS  
 Указывает все поля для `BP_REQUEST_INFO2` структуры.  
  
## <a name="remarks"></a>Примечания  
 Передается в качестве аргумента для [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) и [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) методы, чтобы указать, какие поля из [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) структуры должны быть инициализированы.  
  
 Эти флаги также используются для указания поля `BP_REQUEST_INFO` и `BP_REQUEST_INFO2` структуры являются используемые и допустимым, когда каждая структура возвращается.  
  
 Эти значения могут объединяться с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)

