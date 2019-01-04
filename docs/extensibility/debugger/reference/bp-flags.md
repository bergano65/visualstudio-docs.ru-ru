---
title: BP_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d3739a2edb3f221548f26ee6f03a6f107c01e62
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907687"
---
# <a name="bpflags"></a>BP_FLAGS
Предоставляет необязательные флаги, которые могут использоваться для указания дополнительных сведений при задании точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>Участники  
 BP_FLAG_NONE  
 Задает флаг без точки останова.  
  
 BP_FLAG_MAP_DOCPOSITION  
 Указывает, что модуль отладки (DE) должны сопоставляться с помощью документа положение точки останова. Это значение применимо только к точки останова в скрипт ориентированного исходных файлов таких как Active Server Pages (ASP).  
  
 BP_FLAG_DONT_STOP  
 Указывает, что точка останова должны обрабатываться с помощью обработчика отладки, но что модуль отладки в конечном счете следует останавливает существует (то есть [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) не следует отправлять объект события). Этот флаг предназначен для использования главным образом с использованием точек трассировки.  
  
## <a name="remarks"></a>Примечания  
 Используется для `dwFlags` членом [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) и [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 Эти значения могут объединяться с побитовым объектом `OR`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)